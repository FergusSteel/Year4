```
import random
import networkx as nx
import pulp
import minizinc as mz
import time
import numpy as np
import matplotlib.pyplot as plt
# you will likely need to import other things


#
# This function should run your ILP implementation
# for infectious vaccine 
# - instance_graph will be a networkx graph object
# - start_node is the node where the fire starts
# - timeout is the maximum time in ms you should let the search run for
# The function should return a dictionary that has 'num_saved' mapped to 
# the number saved in the solution
# or None if the model does not halt in the time allowed
# (The dictionary structure is so you can return other things if it's 
# useful for your pipeline)
# What needs to change for infectious defense scneario from constraints given.
def run_ilp(instance_graph, start_node = 1, timeout=1000, verbose=False):
   # Instance graph -> adjacency matrix
  # Variables
  num_vertices = len(instance_graph.nodes)
  G = instance_graph
  # print("ilp ", nx.adjacency_matrix(G))
  T = range(num_vertices)
  root=start_node

  problem = pulp.LpProblem("Infectious_Firefighter", pulp.LpMinimize)

  B = pulp.LpVariable.dicts("B", ((x, t) for x in G.nodes for t in T), 0, 1, pulp.LpBinary)
	  D = pulp.LpVariable.dicts("D", ((x, t) for x in G.nodes for t in T), 0, 1, pulp.LpBinary)
  # objective
  problem += pulp.lpSum(B), "Minimize_B"

  # Constraints, as was implemented in the mz
  # Root is burning at time 0, others are not
  # print(G.nodes)
  
  for x in G.nodes:
    if x != root:
      problem += B[x, 0] == 0
    else:
      problem += B[x, 0] == 1

  # no node goes out/becomes undefended
  for x in G.nodes:
    for t in T[1:]:
      problem += B[x,t] >= B[x,t-1]
      problem += D[x,t] >= D[x,t-1]

  # no node is defended and burning
  for x in G.nodes:
    for t in T:
      problem += B[x,t] + D[x,t] <= 1

  # not sure what this one does but its in the minizinc.
  # for t in T[1:]:
  #   for x in G.nodes:
  #     for y in G.neighbors(x):
  #       problem += B[x,t] + D[x,t] >= B[y,t-1]

  # Burn Spread and Defense Spread
  #Borning
  for t in T[1:]:
    for x in G.nodes:
       for y in G.neighbors(x):
         problem += B[y, t] >= B[x, t - 1] - (D[y, t - 1])
        #  if B[x,t-1] == 1 and D[y,t-1] == 0:
        #    problem += B[y,t] >= B[x,t-1]

  # defundes
  for t in T[1:]:
    for x in G.nodes: 
       for y in G.neighbors(x):
         problem += D[y, t] >= D[x, t - 1] - (B[y, t])
        #  if D[x,t-1] == 1 and B[y,t] == 0:
        #    problem += D[y,t] >= D[x,t-1]

  # Constrain the uhhhh defense spread like i do in minizinc (%  ok this is a wacky one, but it basically says that the increase in defense can be no more than the amount of undefended neighbours for each node and each neighbour)
  for t in T[1:]:
    problem += pulp.lpSum([D[x,t] - D[x,t-1] for x in G.nodes]) <= 1 + pulp.lpSum(pulp.lpSum([1 - D[y,t] for y in G.neighbors(x) for x in G.nodes if D[x,t-1] == 1 and x>y]))

  for x in G.nodes:
    problem += D[x, 0] == 0

  problem.solve(pulp.PULP_CBC_CMD(msg=False))

  if verbose:
    print("Status:", pulp.LpStatus[problem.status])
    for t in T:
      print(f"B@{t} = {[pulp.value(B[x, t]) for x in G.nodes]})")

    for t in T:  
      print(f"D@{t} = {[pulp.value(D[x, t]) for x in G.nodes]})")

  num_saved = num_vertices - sum([pulp.value(B[x, num_vertices-1]) for x in G.nodes])

  # Constraints from normal firefighters - https://camo.githubusercontent.com/af74b581c9c7431ac5efe266ff758e614a4817b714ba9c2b20b27f537cffce93/68747470733a2f2f692e696d6775722e636f6d2f687171566762742e706e67

  return {'num_saved': num_saved}



#
# This function should run your ILP implementation
# for infectious vaccine 
# - instance_graph will be a networkx graph object
# - start_node is the node where the fire starts
# - timeout is the maximum time in ms you should let the search run for
# The function should return a dictionary that has 'num_saved' mapped to 
# the number saved in the solution
# or None if the model does not halt in the time allowed
# (The dictionary structure is so you can return other things if it's 
# useful for your pipeline)
# There are many ways to deal with the instance_graph, and 
# this is intentionally left up to you. 
# For example, you could create a .dzn file in whatever encoding you want
# and add it using the https://python.minizinc.dev/en/latest/api.html#minizinc.model.Model.add_file capability
def run_cp(instance_graph, start_node=1, timeout=1000):
  G = nx.adjacency_matrix(instance_graph)
  # print("cp ",G)
  num_vertices = len(instance_graph.nodes)
  root = start_node

  G_flat = G.todense().flatten().tolist()

  model = mz.Model()
  model.add_file("infectous_firefighter.mzn")

  solver = mz.Solver.lookup("gecode")

  instance = mz.Instance(solver, model)
  dzn = f"root={root};\nnum_vertices={num_vertices};\nG=array2d(1..{num_vertices}, 1..{num_vertices}, {G_flat});"

  instance.add_string(dzn)

  # TIME OUT CODE GOES HERE, and any testing code
  result = instance.solve()
  
  num_saved = int(str(result))

  return {'num_saved': num_saved}


def run_test(N):
  ilp_times = []
  cp_times = []
  failures = 0
  for test_id in range(N):
    # Timer 1
    generate_random_graph = nx.fast_gnp_random_graph(8, 0.2)
    random_root = 1

    

    start_cp = time.time()
    cp = run_cp(generate_random_graph, random_root, 1000)
    cp_duration = time.time() - start_cp
    
    start_ilp = time.time()
    # NEED TO FIX THIS BUT ROOT IS 0 INDEXED IN ILP
    ilp =run_ilp(generate_random_graph, random_root-1, 1000)
    end_ilp = time.time() - start_ilp

    ilp_times.append(end_ilp)
    cp_times.append(cp_duration)

    if cp == ilp:
      print(f"Test {test_id} cp: {cp}, ilp: {ilp}")
      continue
    else:
      print(f"Test {test_id} Failed")
      print(cp)
      print(run_ilp(generate_random_graph, random_root-1, 1000, verbose=False))
      failures += 1
      print(nx.adjacency_matrix(generate_random_graph).todense())
      print(random_root)
      nx.draw(generate_random_graph, with_labels=True)
      plt.show()
    
  print("Test Complete with Failures: ", failures, " our of ", N, " trials.")

  #Performance graphs
  plt.bar("ILP", np.mean(ilp_times))
  plt.bar("CP", np.mean(cp_times))
  plt.show()
  

run_test(5)
```
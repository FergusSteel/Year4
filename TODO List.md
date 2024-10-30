\documentclass{interim}
\usepackage{graphicx}

% alternative font if you prefer
%\usepackage{times}

% for alternative page numbering use the following package
% and see documentation for commands
%\usepackage{fancyheadings}


% other potentially useful packages
%\uspackage{amssymb,amsmath}
%\usepackage{url}
%\usepackage{fancyvrb}
%\usepackage[final]{pdfpages}

\begin{document}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\title{Cross Modal Translation of Musical Performances}
\author{Fergus Steel}
\date{13-12-2024}
\maketitle
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\tableofcontents
\newpage
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\section{Introduction}\label{intro}

briefly explain the context of the project problem

\subsection{A subsection}
Please note your proposal need not follow the included section headings - this is only a suggested structure. Also add subsections etc as required

example references: \cite{BK08}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\section{Statement of Problem}

clearly state the problem to be addressed in your forthcoming project. Explain why it would be worthwhile to solve this problem.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\section{Literature Review}
\textbf{Introduction}
\begin{itemize}
    \item \textbf{Context}: Briefly introduce cross-modal learning in multimodal AI and how it applies to video and audio synthesis, capturing attention with the potential for advancing music generation and the ability to reconstruct musical performances from.
    \item \textbf{Subject and Scope}: Explain the focus on synthesizing emotionally expressive music using visual transformers and generative models, noting the gap in current research in terms of video-to-audio generation in musical performances
    \item \textbf{Structure Overview}: Outline the main themes as bloew .
\end{itemize}

Cross-modal learning denotes integrating diverse sensory modalities as input into a deep learning system, enabling it to process and align information across different types of data sources \cite{baltrušaitis2017multimodalmachinelearningsurvey}. Both vision and audio represent two of the most important sensory channels in human perception, and current aritificial intelligence research has sought to understand how modern deep learning techniques can be leveraged to utilise these modalities in downstream-tasks [EXAMPLES EXAMPLES]. Music encompasses more than what is typically captured in the auditory domain due to its structured and emotional nature. As a result, synthesizing music that embodies distinct structural and semantic elements has become a compelling area of exploration within deep learning [CITE SOTA MUSIC SYNTHESIS PAPERS]. A clear gap in the current literature is investigating the visual component of musical performances. Through integrating different modalities deep learning literature has shown how generative systems can learn to synthesise music that matches the semantic embeddings of visual information [such as Vid2Music AND MORE].

The emotive aspect of music that is captured in a performance, is an aspect of the visual modality that has not currently been captured in the literature. Therefore developing models that can capture the emotional expressiveness inherent in visual performances through cross-modal translation is a significant next step. For instance, while Vid2Music [cite again] and similar models [music2gen + others that i have read] have made strides in synthesising audio representations from visual cues, these models often focus on structural or rhythmic alignment rather than the visual elements conveyed in live performances. By advancing beyond structural mappings, we can aim to synthesize music that resonates with the emotional intensity or subtle expressiveness seen in the visual elements of a performance.

Through directly investigating how the current landscape of computer vision can utilise the visual modality of a musical performance, we gain insight into ways of capturing emotional cues embedded in musicians' expressions, gestures, and environment in the visual modality. We can then use this to develop a cross-modal system capable of learning a shared latent space, that can generate semantically similar music and also capable of inverting this model to reconstruct live performances in the visual domain by utilising these shared representation. Building on these insights, this literature review examines five areas essential for developing a cross-modal system to translate the visual modality of musical performances into expressive synthesised audio. First, exploring how cross-modal learning aligns and embeds video features within audio representations, allowing for translation across modalities. Then, the role of visual transformers is assessed for their capacity to capture the nuanced spatial and temporal details of performances, crucial for transferring emotional depth into synthesized music. Generative models are evaluated for their strengths in producing expressive audio, and we examine the current landscape of audio-visual multi-modal research. Finally, dual-stream models that allow bidirectional audio-video synthesis are discussed to emphasise the potential for providing a comprehensive framework that is capable of translating between modalities more flexibly. Together, these themes outline the current state of research, challenges, and opportunities in cross-modal learning, paving the way for deeper investigation into emotionally rich cross-modal audio-visual embeddings.

\subsection{\textbf{Cross-Modal Representation Learning and Embeddings}}
\begin{itemize}
    \item \textbf{Overview}: Discuss cross-modal translation, specifically how features from one domain (video) are embedded and translated into another (audio).
    \item \textbf{Relevant Studies}:
    \begin{itemize}
        \item Discuss foundational work on multimodal learning and the role of embeddings.
        \item Review studies on how effective cross-modal embeddings can be learned.
    \end{itemize}
\end{itemize}
\textbf{Key Questions}:
\begin{itemize}
    \item How are audio and visual features linked in current models?
    \item What are the main challenges in aligning these modalities?
\end{itemize}

In multi-modal research,  

\paragraph{\textbf{Theme 2: Visual Transformers for Video Understanding}}
\begin{itemize}
    \item \textbf{Overview}: Analyze how visual transformers (e.g., ViViT) capture high-dimensional features from videos, particularly focusing on musical performances.
    \item \textbf{Relevant Studies}:
    \begin{itemize}
        \item Discuss foundational papers on ViTs, such as "ViViT: A Video Vision Transformer".
        \item Include recent work on applying ViTs in multimodal tasks.
    \end{itemize}
\end{itemize}
\textbf{Key Questions}:
\begin{itemize}
    \item What advantages do visual transformers offer for music based video-to-audio tasks?
    \item How do temporal and spatial embeddings factor into visual performance analysis?
    \item Can we incorporate optical flow fields as aditional visual features to improve performance.
\end{itemize}

\paragraph{\textbf{Theme 3: Generative Models for Audio Representation and Music Synthesis}}
\begin{itemize}
    \item \textbf{Overview}: Discuss generative models used for audio synthesis (e.g., diffusion models, GANs) and how they translate visual input into emotionally rich music.
    \item \textbf{Relevant Studies}:
    \begin{itemize}
        \item Papers like "MM-Diffusion: Learning Multi-Modal Diffusion Models" and Meta’s MusicGen for music synthesis.
        \item Compare diffusion models with other generative approaches like GANs.
    \end{itemize}
\end{itemize}
\textbf{Key Questions}:

\begin{itemize}
    \item How well do these models generate expressive music from visual cues?
    \item What trade-offs exist between different audio synthesis techniques?
\end{itemize}

\paragraph{\textbf{Theme 4: Audio-Visual Multi-Modal Models}}
\begin{itemize}
    \item \textbf{Overview}: Focus on what has been done in the audio-visual domain, what is imiliar to what we are working on, why is this model different.
    \item \textbf{Relevant Studies}:
    \begin{itemize}
        \item THE URMP, and other papers that I have already read.
    \end{itemize}
\end{itemize}
\textbf{Key Questions}:

\begin{itemize}
    \item What has been done.
\end{itemize}

\paragraph{\textbf{Theme 5: Dual-Stream Models for Cross-Modal Translation}}
\begin{itemize}
    \item \textbf{Overview}: Discuss dual-stream architectures that allow bidirectional translation between audio and video domains.
    \item \textbf{Relevant Studies}:
    \begin{itemize}
        \item Review "A Two-Stream Neural Network for Audio-Visual Generation".
        \item Discuss applications of these models in reversing the input (audio to video synthesis).
    \end{itemize}
\end{itemize}
\textbf{Key Questions}:
\begin{itemize}
    \item How do dual-stream models balance information between modalities?
    \item Can audio-driven video synthesis be used to assess model performance?
\end{itemize}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\section{Proposed Approach}

state how you propose to solve the software development problem. Show that your proposed approach is feasible, but identify any risks.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\section{Work Plan}

show how you plan to organize your work, identifying intermediate deliverables and dates.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% it is fine to change the bibliography style if you want
\bibliographystyle{plain}
\bibliography{interim}
\end{document}

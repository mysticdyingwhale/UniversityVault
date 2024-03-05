# Rule Ordering
#linguistics 


Some rules apply in environments that are defined phonemically (as opposed to phonetically).

/t/ /d/ -> \[ɾ\] rule turns different underlying forms into same surface form -> neutralization. 


\documentclass{article}

\usepackage{graphicx} % Required for inserting images

\usepackage{amsfonts}

\usepackage{tipa}

\newcommand\setItemnumber[1]{\setcounter{enumi}{\numexpr#1-1\relax}}

\usepackage{amsmath}

\usepackage{titling}

\usepackage{etoolbox}

\usepackage[inline,shortlabels]{enumitem}

  

\usepackage{tabto}

\AfterEndEnvironment{description*}{\hfill\par}

  

\setlength{\droptitle}{-10em}   % This is your set screw

\usepackage{ifluatex,ifxetex}

\ifluatex

  \usepackage{fontspec} % optional

\else\ifxetex

  \usepackage{fontspec} % optional

\else % assume that pdftex engine is in use

  \usepackage[T1]{fontenc}

  \usepackage[utf8]{inputenc} % optional for "\ng"

\fi\fi

  

\newcommand*{\xdash}[1][2em]{\rule[0.5ex]{#1}{0.55pt}}

  

\makeatletter

\newcommand{\Spvek}[2][r]{%

  \gdef\@VORNE{1}

  \left(\hskip-\arraycolsep%

    \begin{array}{#1}\vekSp@lten{#2}\end{array}%

  \hskip-\arraycolsep\right)}

  

\def\vekSp@lten#1{\xvekSp@lten#1;vekL@stLine;}

\def\vekL@stLine{vekL@stLine}

\def\xvekSp@lten#1;{\def\temp{#1}%

  \ifx\temp\vekL@stLine

  \else

    \ifnum\@VORNE=1\gdef\@VORNE{0}

    \else\@arraycr\fi%

    #1%

    \expandafter\xvekSp@lten

  \fi}

\makeatother

\begin{document}

  

\begin{enumerate}

\item .

\item Word-final consonant clusters end in voiceless alveolar fricative [s]. Aspirated stops do not precede voiceless alveolar fricative [s].

\item \begin{enumerate}

\item Nom. Sing. : -s

\item Gen. Sing. : -os

\item Dat. Sing. : -i

\item Dat. Plur. : -si

\end{enumerate}

  

\item Laryngeal Assimilation: $\begin{bmatrix} \text{-son} \\ \text{-cont} \end{bmatrix} \rightarrow \text{[-voice]} \slash \_  \text{[s]} $. Stops devoice before [s]\\ Deaspiration: $\begin{bmatrix} \text{-son} \\ \text{-cont} \end{bmatrix} \rightarrow [\text{-s.g}] \slash \_ \text{[s]}$. Stops deaspirate before [s] \\ Alveolar Deletion: $\begin{bmatrix} \text{COR} \\ \text{+ant} \end{bmatrix} \rightarrow \emptyset \slash \_ \begin{bmatrix} \text{COR} \\ \text{+ant} \end{bmatrix}$ When two alveolars are adjacent, the former is deleted.

  

\item salt: hal \\ vein: p$^{\text{h}}$le:b \\ upper story: kate:lip$^{\text{h}}$ \\ goat: ajg \\ trumpet: salpi\ng \\ nail: onuk$^{\text{h}}$ \\ helmet: korut$^{\text{h}}$ \\ nose: ri:n \\ porpoise: delp$^{\text{h}}$i:n

  

\item 

  

\begin{tabular}{||c c c c||} 

 \hline

 delp$^{\text{h}}$i:n & L.A, Deasp., A.D. & L.A, A.D., Deasp. & delp$^{\text{h}}$i:n \\ [0.5ex] 

 \hline\hline

 L.A. & 6 & 87837 & 787 \\ 

 \hline

 Deasp. & 7 & 78 & 5415 \\

 \hline

 A.D. & 545 & 778 & 7507 \\

 \hline

\end{tabular}

  

\end{enumerate}

  

\end{document}

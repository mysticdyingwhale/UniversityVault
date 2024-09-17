
\documentclass{article}

\usepackage{graphicx} % Required for inserting images

\usepackage{amsfonts}

\usepackage{tipa}

\newcommand\setItemnumber[1]{\setcounter{enumi}{\numexpr#1-1\relax}}

\usepackage{amsmath}

\usepackage{titling}

\usepackage{etoolbox}

\usepackage[inline,shortlabels]{enumitem}

  
\newcommand{\R}{\mathbb{R}}
\newcommand{\F}{\mathbb{F}}
\newcommand{\C}{\mathbb{C}}
\newcommand{\la}{\langle}
\newcommand{\ra}{\rangle}

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
 
\title{Homework 9}

\author{Asaad Al Barwani
\\  Honors Linear Algebra}

\date{April 17 2024}

  

\begin{document}

  

\maketitle

  

\section{7B}

\begin{enumerate}

\item Given that $T^9 = T^8$, we can factor out $T^8$ from both sides to get $T^8(T-I) =0$. \\\\ Since $T$ is a normal operator, by the Spectral Theorem $T$ is diagonizable, so $T$ has a complete set of eigenvectors that span $V$, and for each eigenvector $v$ of $T$, $T^8(T-I)v = 0$. \\\\ Let $v$ be an eigenvector of $T$ with eigenvalue $\lambda$. We have $T^8(T-I)v = T^8(Tv-v) = T^8(\lambda v - v) = T^8(\lambda - 1)v = (\lambda)^8(\lambda-1)v = (\lambda ^ 9 - \lambda ^ 8)v = 0v = 0$ \\\\ Since $v$ is arbitrary this only holds if $\lambda^9 = \lambda ^8$ for all eigenvalues of $T$, and since $(\lambda)^8(\lambda-1) = 0$ $\lambda = 0$ or $\lambda = 1$. 
\item 
\item
\item

\end{enumerate}

\section{7C}

\begin{enumerate}
\setItemnumber{5}

\item 
\item

\end{enumerate}

\section{7D}
\begin{enumerate}
\setItemnumber{7}

\item \begin{enumerate}
\item
\item 
\end{enumerate}
\item  \begin{enumerate}
\item
\item 
\end{enumerate}


\end{enumerate}


\end{document}

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

\title{Homework 2}

\author{Asaad Al Barwani

\\  Honors Linear Algebra}

\date{February 7 2024}

  

\begin{document}

  

\maketitle

  

\section{2A}

  

\begin{enumerate}

  

\item Given $5v_1-4v_2, v_2,v_3,...v_m$, suppose $a_1,...,a_m \in \mathbb{F}$ such that $a_1(5v_1-4v_2)+a_2v_2+...+a_mv_m=0$. \\\\ So $v_1(5a_1)+(a_2-4a_1)v_2+...+a_mv_m=0$. Given that $v_1,...,v_n$ is linearly independent, the only choice of $5a_1,(a_2-4a_1),a_3,...,a_m \in \mathbb{F}$ such that the linear combination is equal to 0 is 0 for all listed scalars. \\\\ So, $5a_1=0,a_2-4a_1=0,a_3=0,...,a_m=0$. Since $5a_1=0, a_1=0$ so $a_2-4a_1=a_2-4(0)=a_2$. So $a_2=0$. Thus, $a_1=a_2=a_3=...=a_m=0$, so $5v_1-4v_2, v_2,v_3,...v_m$ is linearly independent. 

  

\item Given $v_1,v_2,...,v_m$, suppose $a_1,...,a_m \in \mathbb{F}$ such that $a_1(\lambda v_1)+a_2(\lambda v_2)+...+a_m(\lambda v_m)=0$. \\\\ So $v_1(\lambda a_1)+v_2(\lambda a_2)+...+v_m(\lambda a_m)=0$. Given that $v_1,...,v_n$ is linearly independent, the only choice of $\lambda a_1, \lambda a_2, ..., \lambda a_m \in \mathbb{F}$ such that the linear combination is equal to 0 is $\lambda a_k = 0$ for all $k \in \mathbb{F}$. \\\\ So, $\lambda a_1=0, \lambda a_2 = 0, ... \lambda a_m = 0$. Since $\lambda \neq 0$, $a_1=a_2=...=a_m=0$, so $\lambda v_1,\lambda v_2,..., \lambda v_m$ is linearly independent.

  

\item Given a linearly independent set $v_1,...,v_m \in V$ and some $w \in V$, suppose that $v_1+w,v_2+w,...v_m+w$ is linearly independent, then for $a_1,...,a_m \in \mathbb{F}$, $a_1(v_1+w),a_2(v_2+w),...a_m(v_m+w)=0$. \\\\ So, $a_1v_1+a_2v_2+...+a_mv_m+w(a_1+_2+...+a_m)=0$.

\end{enumerate}

\end{document}
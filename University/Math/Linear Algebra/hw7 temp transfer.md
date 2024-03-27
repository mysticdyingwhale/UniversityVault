
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
 
\title{Homework 7}

\author{Asaad Al Barwani
\\  Honors Linear Algebra}

\date{March 27 2024}

  

\begin{document}

  

\maketitle

  

\section{6A}

\begin{enumerate}

\item ($\implies$) An inner product must satisfy the properties of positivity, definiteness, additivity and homogeneity in the first slot, and conjugate symmetry. Assuming $S$ is injective:\\\\
\textbf{Positivity:}  Since $S$ is injective, if $u \neq 0$ then $Su \neq 0$. So, $\la u,u \ra_1 = \la Su, Su \ra > 0$.
\\\\ \textbf{Definiteness:} If $\la u,u \ra_1 = 0$ then $\la Su,Su \ra = 0$, which implies that $Su=0$. Since $S$ is injective, $u=0$.
\\\\ \textbf{Additivity:} Given some $u,v,w \in V, \la u+v,w \ra = \la S(u+v),Sw \ra = \la Su + Sv, Sw \ra = \la Su, Sw \ra + \la Sv, Sw \ra = \la u,w \ra_1 + \la v,w \ra_1$. 
\\\\ \textbf{Homogeneity:} Given $\lambda \in \F$, $\la \lambda u, v \ra_1 = \la S(\lambda u),Sv \ra = \la \lambda Su, Sv \ra = \lambda \la Su,Sv \ra = \lambda \la u,v \ra_1$
\\\\ \textbf{Conjugate Symmetry:} Take $\la u,v \ra_1 = \la Su,Sv \ra = \overline{\la Sv, Su \ra} = \overline{\la v,u \ra_1}$
\\\\ Thus if $S$ is injective all conditions are met.
\\\\ ($\impliedby$) Assuming that $\la .,. \ra_1$ is an inner product on $V$, $S$ is injective if $Su=Sv$ implies that $u=v$. \\\\ We take $\la u-v, u-v \ra_1 = 0$ which implies that $u-v=0$ by definiteness such that $u=v.$ \\\\ Now, take $Su=Sv$ such that $\la Su-Sv, Su-Sv \ra = \la S(u-v), S(u-v)\ra =\la u-v, u-v \ra_1 = 0$. \\\\ This implies that $u=v$, so $S$ must be injective. 


\item \begin{enumerate}
\item We take $\la u+v, u-v \ra = \la u,u \ra - \la v,v \ra - \la u,v \ra + \la v,u \ra = ||u||^2 -||v||^2 + (\la v,u \ra - \la u,v \ra)$. \\\\ Since $V$ is a real inner product space, the inner product is commutative such that $\la u,v \ra = \la v,u \ra$, so $\la v,u \ra - \la u,v \ra = 0$. \\\\ So we have $\la u+v, u-v \ra =||u||^2 -||v||^2$.
\item Assuming $u,v \in V$ have the same norm such that $||u||=||v||$, we take $\la u+v, u-v \ra = ||u||^2 -||v||^2$ (by previous proof). \\\\ If $||u||=||v||$, then $||u||^2=||v||^2$ so $||u||^2 - ||v||^2 = 0$. \\\\ Since $||u||^2 - ||v||^2 = \la u+v, u-v \ra = 0$, we prove that $u+v, u-v$ are orthogonal.
\item A rhombus is a parallelogram comprised of two pairs of two vectors $u,v$ with equal norms $||u|| = ||v||$ such that the diagonals of the rhombus are $u+v, u-v$ (By 6.21). \\\\ By (b) we know that if two vectors $u,v$ have the same norm, $u+v, u-v$ are orthogonal (perpendicular). \\\\ Therefore, the diagonals of a rhombus are perpendicular.
\end{enumerate}
\item \begin{enumerate}
\item Given $u = (\sqrt a,\sqrt b,\sqrt c,\sqrt d), v = (\frac 1 {\sqrt a},\frac 1{\sqrt b},\frac 1{\sqrt c},\frac 1{\sqrt d})$, we define the inner product as the square of the dot product. \\\\ By the Cauchy-Schwarz inequality we have $|\la u,v \ra| \leq ||u|| ||v||$. \\\\ We now have $(u \cdot v)^2 \leq ( u \cdot u)( v \cdot v) \implies (\sqrt a \cdot \frac 1{\sqrt a} + \sqrt b \cdot\frac 1{\sqrt b} + \sqrt c \cdot\frac 1{\sqrt c} + \sqrt d \cdot\frac 1{\sqrt d} )^2 \leq (a+b+c+d)(\frac 1{a}+\frac 1{b}+\frac 1{c}+\frac 1{d})$ \\\\$ \implies (\sqrt a \cdot \frac 1{\sqrt a} + \sqrt b \cdot\frac 1{\sqrt b} + \sqrt c \cdot\frac 1{\sqrt c} + \sqrt d \cdot\frac 1{\sqrt d} )^2 = (1+1+1+1)^2 = 16$ \\\\ Substituting we get $16 \leq (a+b+c+d)(\frac 1{a}+\frac 1{b}+\frac 1{c}+\frac 1{d})$
\item $a=b=c=d=1$
\end{enumerate}
\item LHS $=\frac{(||u||^2 + 2Re\la u,v \ra + ||v||^2 - ||u||^2 +2Re \la u,v \ra -||v||^2)}{4} + \frac{(\la u+iv, u-iv \ra - \la u-iv, u+iv \ra)i}{4}$ 
\\\\
 $ =  \frac{4Re \la u,v \ra}4 + \frac{((\la u,u \ra - \la u,iv \ra + \la iv, u \ra + \la iv,iv \ra) - (\la u,u \ra - \la u,iv \ra - \la iv, u \ra + \la iv,iv \ra))i}{4}$ 
\\\\
$ = Re(\la u,v \ra)+ \frac i4 ((\la u,u \ra - \la u,v \ra i + \la v, u \ra i + \la v,v \ra) - (\la u,u \ra + \la u,v \ra i- \la v, u \ra i + \la v,v \ra))$ \\\\
$= Re(\la u,v \ra)+ \frac i4 ((||u||^2+2iIm(\la u,v \ra)+||v||^2) - (||u||^2 -2i Im(\la u,v \ra) + ||v||^2))$\\\\
$ = Re(\la u,v \ra)+ \frac i4 (4 Im (\la u,v \ra))$\\\\
$ = Re(\la u,v \ra) + i \cdot Im(\la u,v \ra)$\\\\
$ = \la u,v \ra$
\end{enumerate}

\section{6B}

\begin{enumerate}
\setItemnumber{5}

\item .

\item .

\item .

\item .

\end{enumerate}

\end{document}
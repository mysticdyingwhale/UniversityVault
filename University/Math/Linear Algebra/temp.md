
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
 
\title{Homework 8}

\author{Asaad Al Barwani
\\  Honors Linear Algebra}

\date{April 3 2024}

  

\begin{document}

  

\maketitle

  

\section{6C}

\begin{enumerate}

\item By 6.49, any $v \in V$ can be written as the sum of $P_U(v)+P_{U^\perp}(v)$ such that $v = u + w$, $u = P_U(v) \in U, w = P_{U^\perp}(v) \in U^\perp$.
\\\\ Applying $I - P_U$ to $v$, we get $I(v)-P_U(v)= v - P_U(v)$, and substituting our original equality we get $I(v)-P_U(v) =u+w -P_U(v)$. 
\\\\ Since $P_U(v) = u$, we have $I(v)-P_U(v) =u+w -P_U(v) = w = P_{U^\perp}(v)$. 
\\\\ Thus,$I(v)-P_U(v) = w \implies I - P_U = P_{U^\perp}$

\item ($\implies$) We assume that $P_UTP_U = TP_U$. By the properties of $P_U$ we know that $P_U(u) = u$, so applying $T$ to both sides we get $TP_U(u) = T(u)$ for any $u \in U$. 
\\\\ By our assumption we can apply $P_U$ to the right side to get $P_U(T(P_U(u))) = P_U(T(u))$ Since $P_U(u)=u$, we get $P_U(T(u)) = P_U(T(u))$. 
\\\\This shows that $T(u) \in \text{range }(P_U)$. Since $\text{range }(P_U) =U$ by the basic properties of the projection operator, $T(u) \in U$. Thus, $U$ is invariant under $T$. 
\\\\ ($\impliedby$) We assume that $U$ is invariant under $T$ such that $T(u) \in U$. This means that $P_U(T(u))= T(u)$ since for all $u \in U, P_U(u) =u$. 
\\\\ Now, for some arbitrary $v \in V$ we take the case of $T(P_U(v))$. By definition of the projection operator, $P_U(v) \in U$, and since $U$ is invariant under $T$, when we apply $P_U$ to this we can simplify to $P_U(T(P_U(v))) = T(P_U(v))$ as $P_U(u) = u$. 
\\\\ By linearity, we can rewrite this as $P_UTP_U(v) = TP_U(v)$. Since $v$ is arbitrary, $P_UTP_U = TP_U$ holds for all $v \in V$.  

\item ($\implies$) We assume that $P_U T = TP_U$. Then, for any $u \in U$ we have $P_U(T(u)) = TP_U(u) = T(u)$. Since anything applied to $P_U \in U$, $T(u) \in U$. So $U$ is invariant under $T$. 
\\\\ Take some vector $w \in U^\perp$. Since $P_U$ is a projection onto $U$, $P_U(w) = 0$ as $U \cap U^\perp = \{0\}$. So $T(P_U(w)) = T(0) = 0$, which means that $P_U(T(w))= 0$ by our initial assumption. 
\\\\ This means that $T(w)$ is orthogonal  to every vector in $U$, so $T(w) \in U^\perp$ and thus $U^\perp$ is invariant under $T$. 
\\\\ ($\impliedby$) We assume that $U, U^\perp$ are invariant under $T$. For some $v \in V$, by 6.49 we can write $v = u +w$ for some $u \in U, w \in U^\perp$. 
\\\\ Applying $T$ to this equality we get $T(v) = T(u + w) = T(u)+T(w)$ by linearity. Applying $P_U$ gives us $P_U(T(v)) = P_U(T(u)+T(w)) = P_U(T(u))+P_U(T(w))$ by linearity. 
\\\\ Since $U^\perp$ is invariant under $T$, $T(w) \in U^\perp$, so $P_U(T(w)) = 0$. Since  $U$ is invariant under $T$, $T(u) \in U$ so $P_U(T(u)) = T(u)$. This leaves us with $P_U(T(v)) = T(u)$.
\\\\ Applying $P_U$ after $T$ we have $TP_U(v) = TP_U(u+w) = T(P_U(u)+TP_U(w)) = T(u)$, since $P_U(u) = u$ and $P_U(w) = 0$. 
\\\\ So $TP_U(v) = T(u) = P_U(T(v))$, and since $v$ and $u$ are arbitrary we have $TP_U = P_UT$.
\item Since $p \in P_3(\R)$, $p'(0)=0$ and $p(0)=0$, $p(x)$ is in the form of $ax^3+bx^2$.
\\\\Let C[0,1] denote the real inner product space of continuous real valued functions on [0,1] with inner product $<f,g> = \int_0^1 fg$. 
\\\\ Let $v \in C[0,1]$ be the function defined by $v(x) = 2+3x$. 
\\\\We solve for $\la v(x)-p(x), x^2 \ra =0, \la v(x)-p(x), x^3 \ra = 0$: 
\\\\$\int_0^1(v(x)-p(x))x^2 dx =  \int_0^1(v(x)-p(x))x^3 dx = 0$.  
\\\\$=\int_0^1(2+3x-ax^3-bx^2)x^2 dx =  \int_0^1(2+3x-ax^3-bx^2)x^3 dx = 0$. 
\\\\ $= \int_0^1 2x^2+3x^3-ax^5-bx^4 dx = \int_0^1 2x^3+3x^4-ax^6-bx^5 dx = 0$ 
\\\\$ = \frac 23 + \frac 34 - \frac a6 -\frac b5 = \frac 24 +\frac 35 - \frac a7 -\frac b6 = 0$
\\\\$a = -20.3, b= 24$


\end{enumerate}

\section{7A}

\begin{enumerate}
\setItemnumber{5}

\item Since $T$ shifts all vectors to the right by one place,

\item ($\implies$) Assuming $U^\perp$ is invariant under $T^*$, x

\item \begin{enumerate}
\item .
\item .
\end{enumerate}

\item \begin{enumerate}
\item .
\item $T$ is normal, meaning it commutes with its transpose such that $TT^* = T^*T$. Although being self-adjoint implies that $T$ is normal, the opposite is not true, as it can be normal without being self-adjoint as is the case here.
\end{enumerate}

\end{enumerate}

\end{document}
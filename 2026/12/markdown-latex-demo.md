\documentclass[11pt, a4paper]{article}

% Encoding & layout
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage[margin=1in]{geometry}
\usepackage{microtype}

% Math, tables, and figures
\usepackage{amsmath, amssymb}
\usepackage{booktabs}
\usepackage{graphicx}

% Clickable links & references
\usepackage[hidelinks]{hyperref}

% Title metadata
\title{A Practical Guide to Writing LaTeX Articles}
\author{Alex Rivera\thanks{Department of Computer Science, Example University}}
\date{\today}

\begin{document}

\maketitle

\begin{abstract}
This short article demonstrates how to structure a LaTeX document with sections, equations, tables, figures, and bibliography references.
\end{abstract}

\section{Introduction}
Write your opening paragraphs here. Blank lines create new paragraphs automatically; single line breaks do not.

\subsection{Key Concepts}
You can emphasize text with \textbf{bold} or \textit{italics}, and write inline math like $E = mc^2$.

\section{Equations and Data}
Displayed equations get automatic numbering:
\begin{equation}
  \nabla \cdot \mathbf{E} = \frac{\rho}{\varepsilon_0}
\end{equation}

Table~\ref{tab:summary} compares two common document classes.

\begin{table}[htbp]
  \centering
  \caption{Comparison of LaTeX document classes.}
  \label{tab:summary}
  \begin{tabular}{ll}
    \toprule
    Class & Typical Use Case \\
    \midrule
    \texttt{article} & Journal papers, preprints, short reports \\
    \texttt{report}  & Theses, multi-chapter technical reports \\
    \bottomrule
  \end{tabular}
\end{table}

\section{Conclusion}
Summarize your main findings and next steps here.

\end{document}

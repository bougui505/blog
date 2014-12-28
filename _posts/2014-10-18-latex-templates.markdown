---
title: "LaTeX templates"
layout: default
category: LaTeX
date: 2014-10-18 22:43:21 CEST
tags:
- LaTeX
---

- article:

{% highlight latex %}
\documentclass[a4paper,10pt]{article}
\usepackage{graphicx} % for including graphics with easy resizing
\usepackage[utf8x]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[french]{babel} 
\usepackage{times} % font
\author{\textsc{Name} Firstname}
\date{\today} 
\title{Title}


\begin{document}

\maketitle

\begin{abstract}
Abstract
\end{abstract}

Text

\bibliographystyle{apalike}
\bibliography{thebibfile}
\end{document}
{% endhighlight %}

- report:

{% highlight latex %}
\documentclass[a4paper,10pt]{report}
\usepackage{graphicx} % for including graphics with easy resizing
\usepackage[utf8x]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[french]{babel} 
\usepackage{times} % font
\usepackage{makeidx}
\title{Le titre}
\author{\textsc{Name} Firstname}
\date{\today}

\makeindex
\begin{document}

\maketitle

\begin{abstract}
Abstract
\end{abstract}


\tableofcontents


The \index{text}

\listoffigures
\listoftables
\printindex
\end{document}
{% endhighlight %}

- book:

{% highlight latex %}
\documentclass{book}
\usepackage{graphicx} % for including graphics with easy resizing
 
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[french]{babel} 
\usepackage{times} % font
\usepackage{makeidx}
\makeindex
\title{Le titre}
\author{\textsc{Name} Firstname}
\date{\today}  
 
\begin{document}
 
\maketitle

\frontmatter 

Introductive part

\mainmatter

Text body

\appendix
Supplementary material   
\bibliographystyle{}
\bibliography{bibli}

\backmatter

Epilogue

\tableofcontents
\listoffigures
\listoftables
\printindex

\end{document}
{% endhighlight %}

- letter:

{% highlight latex %}
\documentclass{letter}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[francais]{babel}
\usepackage{times}

\signature{M. Laleloulilo (signature)}
\address{Première ligne de l'adresse \\ Deuxième ligne \\ Troisième ligne}
\begin{document}
\begin{letter}{Un destinataire\\Un autre \\ Son copain & son lapin \\ 
ligne d'adresse 1 \\ ligne d'adresse 2 \\ ligne d'adresse 3}
\opening{Formule de politesse d'ouverture,}

Le texte.
 
\closing{Cordialement, (formule de politesse)}
\ps{P.-S. : Votre petit ajout ! :-)}
 
\end{letter}
 
\end{document}
{% endhighlight %}

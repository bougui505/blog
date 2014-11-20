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
\usepackage{times} % Pour changer le pack de police
\author{\textsc{Nom} Prénom}
\date{\today} 
\title{Mon titre d'article}


\begin{document}

\maketitle

\begin{abstract}
Le résumé (abstract en anglais) de mon article.
\end{abstract}

Bla bla bla


\end{document}
{% endhighlight %}

- report:

{% highlight latex %}
\documentclass[a4paper,10pt]{report}
\usepackage{graphicx} % for including graphics with easy resizing
\usepackage[utf8x]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[french]{babel} 
\usepackage{times} % Pour changer le pack de police
\usepackage{makeidx}
\title{Le titre}
\author{\textsc{Nom} Prénom}
\date{} % Pour mettre la date du jour, tapez \today 

\makeindex
\begin{document}

\maketitle

\begin{abstract}
Le résumé (abstract en anglais) de mon article.
\end{abstract}


\tableofcontents


Bla\index{bla} bla bla

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
\usepackage{times} % Pour changer le pack de police
\usepackage{makeidx}
\makeindex
\title{Le titre}
\author{\textsc{Nom} Prénom}
\date{\today}  
 
\begin{document}
 
\maketitle % Page de garde

\frontmatter 

Pages introductives

\mainmatter

Contenu

\appendix
   
Chapitres annexes
\bibliographystyle{} % Le style est mis entre crochets.
\bibliography{bibli} % Mon fichier de base de données s'appelle bibli.bib.

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

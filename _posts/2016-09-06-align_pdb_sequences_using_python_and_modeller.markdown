---
title: "Align pdb sequences using python and Modeller"
layout: default
date: 2016-09-06
tags:
- python
- science
- modeller
---

# Align pdb sequences using python and Modeller

Usage:

    ./align_pdb_seq.py pdb1 pdb2 [...]

Example output:

    $ ./align_pdb_seq.py 148l.pdb 2lcb.pdb

                             MODELLER 9.16, 2016/01/07, r10745

         PROTEIN STRUCTURE MODELLING BY SATISFACTION OF SPATIAL RESTRAINTS


                         Copyright(c) 1989-2016 Andrej Sali
                                All Rights Reserved

                                 Written by A. Sali
                                   with help from
                  B. Webb, M.S. Madhusudhan, M-Y. Shen, G.Q. Dong,
              M.A. Marti-Renom, N. Eswar, F. Alber, M. Topf, B. Oliva,
                 A. Fiser, R. Sanchez, B. Yerkovich, A. Badretdinov,
                         F. Melo, J.P. Overington, E. Feyfant
                     University of California, San Francisco, USA
                        Rockefeller University, New York, USA
                          Harvard University, Cambridge, USA
                       Imperial Cancer Research Fund, London, UK
                  Birkbeck College, University of London, London, UK


    Kind, OS, HostName, Kernel, Processor: 4, Linux mantrisse 3.16.0-4-amd64 x86_64
    Date and time of compilation         : 2016/01/07 09:23:18
    MODELLER executable type             : x86_64-intel8
    Job starting time (YY/MM/DD HH:MM:SS): 2016/09/06 12:36:19


    SALIGN_____> adding the next group to the alignment; iteration    1
     _aln.pos         10        20        30        40        50        60
    148l      MNIFEMLRIDEGLRLKIYKDTEGYYEIGIGHLLTKSPSLNAAKSELDKAIGRNTNGVITKDEAEKLFN 
    2lcb      MNIFEMLRIDEGLRLKIYKDTEGYYTIGIGHLLTKSPSLNAAKSELDKAIGRNTNGVITKDEAEKLFN 
     _consrvd ************************* ******************************************

     _aln.p   70        80        90       100       110       120       130
    148l      QDVDAAVRGILRNAKLKPVYDSLDAVRRAALINMVFQMGETGVAGFTNSLRMLQQKRWDEAAVNLAKS 
    2lcb      QDVDAAVRGILRNAKLKPVYDSLDAVRRAAAINMVFQMGETGVAGFTNSLRMLQQKRWDEAAVNLAKS 
     _consrvd ****************************** *************************************

     _aln.pos  140       150       160
    148l      RWYNQTPNRAKRVITTFRTGTWDAYKN/A 
    2lcb      RWYNQTPNRAKRVITTFRTGTWDAYKN-L 
     _consrvd ***************************

{% gist 5226ec7909da1760c91f5159216af7f8 %}

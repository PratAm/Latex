## Latex

Latex code to generate the resume 

If you're using a distro which packages LaTeX (almost all will do) then look for texlive

       apt-get install texlive

Next you'll need to get a text editor. Any editor will do, so whatever you are comfortable with. You'll find that advanced editors like Emacs (and vim) add a lot of functionality and so will help with ensuring that your syntax is correct before you try and build your document output.

Create a file called test.tex and put some content in it, say the example from the LaTeX primer:

\documentclass[a4paper,12pt]{article}
\begin{document}

The foundations of the rigorous study of \emph{analysis}
were laid in the nineteenth century, notably by the
mathematicians Cauchy and Weierstrass. Central to the
study of this subject are the formal definitions of
\emph{limits} and \emph{continuity}.

Let $D$ be a subset of $\bf R$ and let
$f \colon D \to \mathbf{R}$ be a real-valued function on
$D$. The function $f$ is said to be \emph{continuous} on
$D$ if, for all $\epsilon > 0$ and for all $x \in D$,
there exists some $\delta > 0$ (which may depend on $x$)
such that if $y \in D$ satisfies
\[ |y - x| < \delta \]
then
\[ |f(y) - f(x)| < \epsilon. \]

One may readily verify that if $f$ and $g$ are continuous
functions on $D$ then the functions $f+g$, $f-g$ and
$f.g$ are continuous. If in addition $g$ is everywhere
non-zero then $f/g$ is continuous.

\end{document}

Once you've got this file you'll need to run latex on it to produce some output (as a .dvi file to start with, which is possible to convert to many other formats):

=> latex test.tex

This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./test.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf/tex/latex/base/size12.clo))
No file test.aux.
[1] (./test.aux) )
Output written on test.dvi (1 page, 1508 bytes).
Transcript written on test.log.
..don't worry about most of this output -- the important part is the Output written on test.dvi line, which says that it was successful.

Now you need to view the output file with xdvi:

xdvi test.dvi &
This will pop up a window with the beautifully formatted output in it. Hit `q' to quit this, or you can leave it open and it will automatically update when the test.dvi file is modified (so whenever you run latex to update the output).

To produce a PDF of this you simply run pdflatex instead of latex:

pdflatex test.tex
..and you'll have a test.pdf file created instead of the test.dvi file.

After this is all working fine, I would suggest going to the the LaTeX primer page and running through the items on there as you need features for documents you want to write.

Future things to consider include:

Use tools such as xfig or dia to create diagrams. These can be easily inserted into your documents in a variety of formats. Note that if you are creating PDFs then you shouldn't use EPS (encapsulated postscript) for images -- use pdf exported from your diagram editor if possible, or you can use the epstopdf package to automatically convert from (e)ps to pdf for figures included with \includegraphics.

Start using version control on your documents. This seems excessive at first, but being able to go back and look at earlier versions when you are writing something large can be extremely useful.

Use make to run latex for you. When you start on having bibliographies, images and other more complex uses of latex you'll find that you need to run it over multiple files or multiple times (the first time updates the references, and the second puts references into the document, so they can be out-of-date unless you run latex twice...). Abstracting this into a makefile can save a lot of time and effort.

Use a better editor. Something like Emacs + AUCTeX is highly competent. This is of course a highly subjective subject, so I'll leave it at that (that and that Emacs is clearly the best option :)

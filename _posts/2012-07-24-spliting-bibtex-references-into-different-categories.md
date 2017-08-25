---
layout: post
title: Spliting BibTeX references into different categories
redirect_from: /2012/07/spliting-bibtex-references-into-different-categories
---

<!--:en-->
<p>I tend to write all my academic papers in LaTeX. I like the idea of it, I like the separation of content and style, I think the output looks good *most* of the times, and, above all, I think managing bibliography with latex is the best option so far.</p>

<p>This post is about managing references. Specifically, about when you want to split your latex references in different categories. Maybe you'd like to list Books and Journals apart from other references, maybe you're writing a review, a state-of-the-art analysis, and you'd like to separate the analyzed works from others you cite along. I had to do both, and found a few different options.</p>

<p>So, here they are:</p>

### 1. Using different .bib files for each category
Package: <a href="http://www.ctan.org/pkg/bibtopic">bibtopic</a>  
Manual: <a href="http://mirror.ctan.org/macros/latex/contrib/bibtopic/bibtopic.pdf">http://mirror.ctan.org/macros/latex/contrib/bibtopic/bibtopic.pdf</a>

Example:
{% highlight tex lineno %}
\documentclass{article}
\usepackage{bibtopic}

\begin{document}
 \bibliographystyle{alpha}
\section{Citing things}
\cite{somebook}. \cite{otherbook}, \cite{somepaper}.
 
% File books.bib is used for this listing:
\begin{btSect}{books}
\section{References from books}
\btPrintCited
\end{btSect}

% File articles.bib is used here, and the listing is in 
% plain-format instead of the standard alpha:
\begin{btSect}[[plain]]{articles}
\section{References from articles}
\btPrintCited
\section{Articles not cited}
\btPrintNotCited
\end{btSect}

% Print all entries from internet.bib:
\begin{btSect}{Internet}
\section{References from teh Internets}
\btPrintAll
\end{btSect}
\end{document}
{% endhighlight %}

### 2. Using a single .bib, and manually separating references using different citation commands

Package: <a href="http://www.ctan.org/pkg/multibib">multibib</a>  
Manual: <a href="http://mirror.ctan.org/macros/latex/contrib/multibib/multibib.pdf">http://mirror.ctan.org/macros/latex/contrib/multibib/multibib.pdf</a>

This creates a different citation command ("citesel" in the example) for each category other than the
default one.

Example:
{% highlight tex lineno %}
\documentclass{article}
\usepackage{multibib}
\newcites{sel}{Selected works}

\begin{document}
\cite{ref1}
\citesel{ref2}

% Selected works (refs.bib)
\bibliographystylesel{spmpsci}
\bibliographysel{refs}

% Other (refs.bib)
\bibliographystyle{spmpsci}
\bibliography{refs}

\end{document}
{% endhighlight %}

### 3. Split based on reference properties

Package: <a href="http://www.ctan.org/pkg/biblatex">biblatex</a>  
Manual: <a href="http://mirror.ctan.org/macros/latex/contrib/biblatex/doc/biblatex.pdf">http://mirror.ctan.org/macros/latex/contrib/biblatex/doc/biblatex.pdf</a>

You can use other properties than type to filter them. You should read the manual if that's the case!

Example:
{% highlight tex lineno %}
\documentclass{article}
\usepackage[defernumbers=true]{biblatex}

\addbibresource{\refs.bib}
\nocite{*}

\begin{document}

\printbibliography[title={Books},type=book]
\printbibliography[title={Other References},nottype=book]

\end{document}
{% endhighlight %}
<!--:--><!--:pt-->

And that's it! Below is the PT-BR version of this article ;)

---------------

# Dividindo referências BibTeX em diferentes categorias

<p>Eu costumo escrever meus artigos acadêmicos usando LaTeX. Eu gosto da ideia dele, gosto da separação de conteúdo e estilo, e acho que o resultado final fica ótimo na maioria das vezes. Acima de tudo, eu acho que gerenciar referências usando latex é a melhor opção que temos até agora.</p>

<p>Esse post é sobre isso: gerenciar referências. Especificamente sobre quando você precisa dividir suas referências em diferentes categorias. Talvez você queira listar os livros e journals separados das outras referências, talvez você esteja escrevendo uma análise do estado-da-arte e quer separar os trabalhos analisados de outras citações. Eu já precisei fazer os dois, e encontrei algumas opções para fazer essa divisão.</p>

<p>Aqui vão elas:</p>

### 1. Usando um arquivo .bib para cada categoria
Pacote: <a href="http://www.ctan.org/pkg/bibtopic">bibtopic</a>
Manual: <a href="http://mirror.ctan.org/macros/latex/contrib/bibtopic/bibtopic.pdf">http://mirror.ctan.org/macros/latex/contrib/bibtopic/bibtopic.pdf</a>

Exemplo:
{% highlight tex lineno %}
\documentclass{article}
\usepackage{bibtopic}

\begin{document}
 \bibliographystyle{alpha}
\section{Citing things}
\cite{um_livro}. \cite{outro_livro}, \cite{um_paper}.
 
% O arquivo books.bib é usado aqui:
\begin{btSect}{books}
\section{Referências de livros}
\btPrintCited
\end{btSect}

% O arquivo articles.bib é usado aqui, e as refs
% são formatadas no estilo "plain" em vez de "alpha":
\begin{btSect}[[plain]]{articles}
\section{Referências de artigos}
\btPrintCited
\section{Artigos não-citados}
\btPrintNotCited
\end{btSect}

% Coloca todas as entradas do arquivo internet.bib:
\begin{btSect}{Internet}
\section{Referências das Internets}
\btPrintAll
\end{btSect}
\end{document}
{% endhighlight %}

### 2. Usando um único .bib, e separando manualmente as referências usando comandos de citação diferentes

Pacote: <a href="http://www.ctan.org/pkg/multibib">multibib</a>
Manual: <a href="http://mirror.ctan.org/macros/latex/contrib/multibib/multibib.pdf">http://mirror.ctan.org/macros/latex/contrib/multibib/multibib.pdf</a>

Esse pacote cria diferentes comandos de citação ("citesel' no exemplo) para cada categoria diferente da padrão.

Exemplo:
{% highlight tex %}
\documentclass{article}
\usepackage{multibib}
\newcites{sel}{Trabalhos selecionados}

\begin{document}
\cite{ref1}
\citesel{ref2}

% Trabalhos selecionados (refs.bib)
\bibliographystylesel{spmpsci}
\bibliographysel{refs}

% Outras referências (refs.bib)
\bibliographystyle{spmpsci}
\bibliography{refs}

\end{document}
{% endhighlight %}

### 3. Divisão baseada em propriedades das referências

Pacotee: <a href="http://www.ctan.org/pkg/biblatex">biblatex</a>
Manual: <a href="http://mirror.ctan.org/macros/latex/contrib/biblatex/doc/biblatex.pdf">http://mirror.ctan.org/macros/latex/contrib/biblatex/doc/biblatex.pdf</a>

Você pode usar outras propriedades para filtrar além do tipo. O manual é bem completo!

Exemplo:
{% highlight tex lineno %}
\documentclass{article}
\usepackage[defernumbers=true]{biblatex}

\addbibresource{\refs.bib}
\nocite{*}

\begin{document}

\printbibliography[title={Livros},type=book]
\printbibliography[title={Outras referências},nottype=book]

\end{document}
{% endhighlight %}<!--:-->

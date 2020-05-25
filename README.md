# LaTeX Tutorial

This part will explain the LaTeX document structure and how to create a title page

<!-- MDTOC maxdepth:6 firsth1:0 numbering:1 flatten:0 bullets:0 updateOnSave:1 -->

1. [The Layout of a LaTeX File](#the-layout-of-a-latex-file)   
2. [The Title Page](#the-title-page)   

<!-- /MDTOC -->

## The Layout of a LaTeX File

To create a document in LaTeX, we need a plain text file that ends with the extension '_.tex_'. This file contains the LaTeX code and the actual contents of the document. The LaTeX compiler takes _.tex_ as input and compiles it into _.pdf_ file.

The _.tex_ file can be divided into two main parts:

1. The preamble of a Document
2. Document

Let's take a look at the contents of a very simple _.tex_ file:

```
\documentclass[12pt, letter]{article}
\usepackage[utf8]{inputenc}

\begin{document}
  Hello World!
\end{document}
```

The part of the _.tex_ file before the `\begin{document}` is called the preamble. In LaTeX, we use commands to define how the document should be formatted and every command starts with the backslash \. The typical structure of the LaTeX command is `\commandname{options}`. The preamble part of the _.tex_ file contains commands, load extra packages, and set different parameters. In the above block of code we define document class as an article.

Other options for the document class are report, letter, book, and beamer. The additional parameters can be defined inside the brackets in a comma-separated fashion. Here the font and paper size are defined.

The actual text of the document, including paragraphs, tables and images etc., goes between the `\begin{document}` and `\end{document}`. Update the above block of code as follows:

```
\documentclass[12pt, letter]{article}
\usepackage[utf8]{inputenc}

\begin{document}
  \section{This is First Level Heading}
  This is the first level heading.

  \subsection{This is Second Level Heading}
  This is the second-level heading.

  \subsubsection{This is Third Level Heading}
  This is the third level heading.
\end{document}
```

Compile the document in the editor and have a look at the pdf document.

## The Title Page

The contents of the title page should be placed in the preamble. Let's define some contents for the title page:

```
\title{This is Title of the Document}
\author{Author's Name}
\date{25 May 2020}
```

Now we need to use `\maketitle` after the `\begin{document}` to display the title page. However, this will start writing the document from the title page, just after finishing the title page contents.

If you want to start writing the document on the next page, use `titlepage` [environment](https://texfaq.org/FAQ-whatenv). Place the following block of code just after the `\begin{document}`

```
\begin{titlepage}
\maketitle
\end{titlepage}
```

By default the article class starts page numbering from the title page. However you can remove the page number from the title page using the command `\thispagestyle{empty}` after the `\maketitle` command:

```
\begin{titlepage}
\maketitle
\thispagestyle{empty}
\end{titlepage}
```

In the date command you can use the current date instead of the manual one by using the `\data{\today}` command.

# LaTeX Tutorial

This part will explain how to create tables and lists

## Create Tables

In `LaTeX`, we can use `table`, `tabular`, or a combination of both environments to create tables. The `table` environment provides additional functionality such as positioning, caption, label, and reference for the table. Whereas, the actual contents go inside the `tabular` environment.

We will start creating the very simplest table and then gradually develop it according to our choice. A simple table can be created using the `tabular` environment which is the default method to create tables in LaTeX. The following block of code creates a very simple table with three columns and text-centered.

```
\begin{center}
  \begin{tabular}{c c c}
    aa & bb & cc \\
    11 & 22 & 33
  \end{tabular}
\end{center}
```

The `{ c c c }` specifies the number of columns and position of text inside the columns. We can also use `l` and `r` to align the text to left and right respectively. The `&` is used to mark the column and `\\` is used to insert a new row.

Let's add some styles to our table to keep the information organized. We will add vertical lines to the columns to separate them from each other by using `{ |c|c|c| }`. Also, we will add a horizontal line at the top and bottom of the table with the use of `\hline`.

The code at this point will look like this:

```
\begin{center}
  \begin{tabular}{ |c|c|c| }
    \hline
    aa & bb & cc \\
    \hline
    11 & 22 & 33 \\
    \hline
  \end{tabular}
\end{center}
```

### Positioning, Caption, Label and Reference the Table

To add additional features like positioning, caption, label, and reference the table, we will be using `table` environment that acts as a wrapper for the `tabular` environment.

For positioning the table, we need to put the table inside `table` float environment.

```
\begin{table}[h!]
  \centering
  \begin{tabular}{ |c|c|c| }
    \hline
    aa & bb & cc \\
    \hline
    11 & 22 & 33 \\
    \hline
  \end{tabular}
\end{table}
```

`[h!]` will place the table here overriding the default LaTeX behavior. You may find the details of other specifiers [here](https://github.com/m-yahya/latex-tutorial/tree/02-insert-images#using-the-figure-environment).

Similarly, we can add a caption and label using `\caption{}` and `label{}` commands respectively within the same `table` environment. The `\ref` and `\label` then can be used to reference the table inside the document.

```
\begin{table}[h!]
    \centering
    \caption{A Simple Table with Caption and Label}
    \label{table1}
    \begin{tabular}{ |c|c|c| }
        \hline
        aa & bb & cc \\
        \hline
        11 & 22 & 33 \\
        \hline
    \end{tabular}
\end{table}
```

Finally, create a list of tables by using the `\listoftables` after the `\begin{document}`.

## Create Lists

In this section, we will take a look to create different types of lists and how to customize list styles.

In general, we can create the following different types of lists in `LaTeX`:

* Unordered lists
* Ordered lists
* Nested lists

### Un-ordered Lists

In LaTeX, an unordered list is created using the `itemize` environment and then place each entry inside the environment using `\item`.

```
\begin{itemize}
    \item The un-numbered item in the list
    \item Another un-numbered item in the list
    \item One more un-numbered item in the list
\end{itemize}
```

### Ordered Lists

An ordered list can be created using the `enumerate` environment and then placing the entries inside the environment.

```
\begin{enumerate}
    \item The first item in the list
    \item The second item in the list
    \item The third item in the list
\end{enumerate}
```

### Nested Lists

In `LaTex`, a list can contain another list as its item. In other words, we can create nested lists in LaTeX. The following block of code shows an example of a nested list:

```
\begin{enumerate}
    \item The first item in the list
    \item The second item in the list
          \begin{enumerate}
            \item sub-item a
            \item sub-item b
            \item sub-item c
          \end{enumerate}
    \item The third item in the list
\end{enumerate}
```

### Customizing List Style

**Unordered List**

By default, LaTeX uses a black dot for bullet points in an un-numbered list. This default behavior can be changed to bold dash, dash, and asterisk in the following way:

```
\begin{itemize}
    \item[--] Dash item
    \item[$-$] Bold Dash item
    \item[$\ast$] Asterisk item
\end{itemize}
```

**Ordered List**

The numbering style for the ordered list can be changed to `Roman`, `Arabic`, and `Alphabetical` using the `enumitem` package as given below. 

```
\documentclass[12pt, letter]{article}
\usepackage{enumitem}
% other packages

\begin{document}


\begin{enumerate}[label=\roman*]
    \item The first item with Roman numbers
    \item The second item with Roman numbers
    \item The third item with Roman numbers
\end{enumerate}

\begin{enumerate}[label=(\arabic*)]
    \item The first item with Arabic numbers
    \item The second item with Arabic numbers
    \item The third item with Arabic numbers
\end{enumerate}

\begin{enumerate}[label=(\alph*)]
    \item The first item with Alphabetical numbers
    \item The second item with Alphabetical numbers
    \item The third item with Alphabetical numbers
\end{enumerate}

\end{document}
```

## Contributing

Pull requests are welcome.

1.  Fork the repository.
2.  Create your new feature branch: git checkout -b new-feature-branch
3.  Stage your changes: git add .
4.  Commit the changes: git commit -m "add commit message"
5.  push to the branch: git push origin new-feature-branch
6.  Submit a pull request.

## License

This project is licensed under the [MIT](./LICENSE) License.
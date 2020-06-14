# LaTeX Tutorial

This part will explain how to add images, create tables and lists

<!-- MDTOC maxdepth:6 firsth1:0 numbering:1 flatten:0 bullets:0 updateOnSave:1 -->

1. [Adding Images](#adding-images)   
&emsp;1.1. [Advanced Image setup](#advanced-image-setup)   
&emsp;&emsp;1.1.1. [Scalling Image Width and Height](#scalling-image-width-and-height)   
&emsp;&emsp;1.1.2. [Using the Figure Environment](#using-the-figure-environment)   
2. [Contributing](#contributing)   
3. [License](#license)   

<!-- /MDTOC -->

## Adding Images

To use images in the LaTeX document, we need to use a package called `graphicx`. To use the `graphicx` package, add the following command in the preamble of your `.tex` file:

```
\usepackage{graphicx}
```

Before adding images to the document, let's create an `images` directory that will keep all the images to be included in the document and add some images to it. We can define the path of the newly created `images` directory by adding the following command in the preamble:

```
\usepackage{graphicx}
\graphicspath{ {./images/} }
```

By using the above command, we specify that `images` is the folder in the current workking directory that contains images to include and thus the compiler will look for this folder to add images. Let's say there is an image named `latex-logo` inside the `images` directory, use the following command to add this image to the document:

```
\includegraphics{latex-logo}
```

It is important that there must be no space within the image name.
We can also specify the image file extension, for example `latex-logo.png`, but omitting the extension will allow LaTeX to search for compatible formats in the `images` folder.

### Advanced Image setup

LaTeX offers multiple options to configure the images to make them presentable in a way you want. In the next section, we will take a look at some more commonly used image configurations.

#### Scalling Image Width and Height

We can adjust width and height of the image in the following ways:

- Set the image size with respect to its original size: use the option `scale` to adjust the size of the image with respect to its original size.

```
\includegraphics[scale=2]{latex-logo}
```

- Use the measurement units: We can use the measurement units to specify height and width of the image.

```
\includegraphics[width=5cm, height=4cm]{latex-logo}
```

It is important to note that if we only specify one parameter, for example width, the height will be adjusted accordingly to keep the aspect ratio intact.

```
\includegraphics[width=5cm]{latex-logo}
```

- Set the size with respect to a document element: We can set the width and height parameters with respect to some other elements of the document. For example, the following command will set the width of the image to width of the text in the document.

```
\includegraphics[width=\textwidth]{latex-logo}
```

#### Using the Figure Environment

We will make use of the `figure` environment to enable some additional features such as image positioning, image labels, captions and references etc. This environment displays the images as floating elements within the document and automatically adjust their placement according to the flow of the document.

The `figure` environment starts with `\begin{figure}` and ends with `\end{figure}` command.

- Positioning the Images: The following command will make use of the `figure` environment to place the figure as floating point. Additionally, we can use `\centering` command to align the image in the center of the document (default is left align).

```
\begin{figure}[h]
\includegraphics[width=\textwidth]{latex-logo}
\centering
\end{figure}
```

In the above block of code, we are placing the image at approximately the same point it occurs in the text by using float value in the form of an additional parameter `[h]`. The other float values that can be used to position the image are explained in the table below:

| Float Value |  Float Name   | Description                                               |
| :---------- | :-----------: | --------------------------------------------------------- |
| !           |   Override    | Forcefully apply the specified float value                |
| b           |    Bottom     | Place the image on the bottom of the page                 |
| h           |     Here      | Place the image where the image command is specified      |
| H           | Strictly here | Strictly place the image at the location of image command |
| p           |     Page      | Place the image on an extra page                          |
| t           |      Top      | Place the image on the top of the page                    |

The combination of override `!` with other float values will forcefully apply the specified float value. For example `[h!]` will forcefully place the image at the position of the image command in the `.tex` file.

- Adding Captions: Captions can be added to briefly describe the images using `\caption` command. The position of caption, below or above the image, is determined by the placement of `\caption` command. If the `\caption` command is place before the `\\includegraphics` command, the caption will appear above the image and vice verca.

```
\begin{figure}[h]
\includegraphics[width=\textwidth]{latex-logo}
\caption{This is LaTeX project logo}
\centering
\end{figure}
```

- Adding Labels: Labels are usefull for cross referencing the images in the document. A label can be added to the image by using the `\label` command and then use that label to refer the image in the document.

```
\begin{figure}[h]
\includegraphics[width=\textwidth]{latex-logo}
\caption{This is \LaTeX\ project logo}
\label{logo}
\centering
\end{figure}

The figure \ref{logo} show the \LaTeX\ project logo on page \pageref{logo}.
```

`\ref` command refers the image and `\pageref` command prints the page number where the reffered image is placed.

Note: you may need to click the run button twice to print the page numbers in the document.

Finally, we can generate list of figure by using the `\listoffigures` commands after the `\begindocument`.

The full code uptill this point is:

```
\documentclass[12pt, letter]{article}
\usepackage[utf8]{inputenc}

\usepackage{graphicx}
\graphicspath{ {images/} }

\begin{document}
\listoffigures
\newpage

\section{Adding Images}
Below is the logo of \LaTeX\ project.

\begin{figure}[h]
\includegraphics[width=\textwidth]{latex-logo}
\caption{This is \LaTeX\ project logo}
\label{logo}
\centering
\end{figure}

The figure \ref{logo} show the \LaTeX\ project logo on page \pageref{logo}.

\end{document}
```

## Contributing

Pull requests are welcome.

1. Fork the repository.
2. Create your new feature branch: git checkout -b new-feature-branch
3. Stage your changes: git add .
4. Commit the changes: git commit -m "add commit message"
5. push to the branch: git push origin new-feature-branch
6. Submit a pull request.

## License

This project is licensed under the [MIT](./LICENSE) License.

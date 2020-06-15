# LaTeX Tutorial

This part will explain how to add images, create tables and lists

<!-- MDTOC maxdepth:6 firsth1:0 numbering:1 flatten:0 bullets:0 updateOnSave:1 -->

1. [Adding Images](#adding-images)  
   &emsp;1.1. [Advanced Image setup](#advanced-image-setup)  
   &emsp;&emsp;1.1.1. [Scalling Image Width and Height](#scalling-image-width-and-height)  
   &emsp;&emsp;1.1.2. [Using the Figure Environment](#using-the-figure-environment)  
   &emsp;&emsp;1.1.3. [Adding Multiple Images](#adding-multiple-images)  
   &emsp;&emsp;1.1.4. [Wrapping Text around the Image](#wrapping-text-around-the-image)
2. [Contributing](#contributing)
3. [License](#license)

<!-- /MDTOC -->

## Adding Images

In LaTeX, images are automatically indexed and tagged with successive numbers when we use the `figure` environment in combination with `graphicx` package. To use images in the LaTeX document, we need to use a package called `graphicx`. To use the `graphicx` package, add the following command in the preamble of the `.tex` file:

```
  \usepackage{graphicx}
```

Before adding images to the document, let's create an `images` directory that will keep all the images to be included in the document and add some images to it. We can define the path of the newly created `images` directory by adding the following command in the preamble:

```
  \usepackage{graphicx}
  \graphicspath{ {./images/} }
```

The command takes one mandatory parameter, the image path in the curly braces, and an optional image width parameter in square brackets. By using the above command, we specify that `images` is the folder in the current working directory that contains images to include, and thus the compiler will look for this folder to add images. Let's say there is an image named `latex-logo` inside the `images` directory, use the following command to add this image to the document:

```
  \includegraphics{latex-logo}
```

It is important that there must be no space within the image name.
We can also specify the image file extension, for example, `latex-logo.png`, but omitting the extension will allow LaTeX to search for compatible formats in the `images` folder.

### Advanced Image setup

LaTeX offers multiple options to configure the images to make them presentable in a way you want. In the next section, we will take a look at some more commonly used image configurations.

#### Scaling Image Width and Height

We can adjust the width and height of the image in the following ways:

- **Set the image size with respect to its original size:** use the option `scale` to adjust the size of the image with respect to its original size.

  ```
   \includegraphics[scale=2]{latex-logo}
  ```

- **Use the measurement units:** We can use the measurement units to specify the height and width of the image.

  ```
   \includegraphics[width=5cm, height=4cm]{latex-logo}
  ```

It is important to note that if we only specify one parameter, for example the width only, the height will be adjusted accordingly to keep the aspect ratio intact.

```
   \includegraphics[width=5cm]{latex-logo}
```

- **Set the size with respect to a document element:** We can set the width and height parameters with respect to some other elements of the document. For example, the following command will set the width of the image to the width of the text in the document.

  ```
     \includegraphics[width=\textwidth]{latex-logo}
  ```

Another option that we can use is `\linewidth` which will scale the image to fit the size of the document.

#### Using the Figure Environment

We will make use of the `figure` environment to enable some additional features such as image positioning, image labels, captions, and references, etc. This environment displays the images as floating elements within the document and automatically adjust their placement according to the flow of the document. Also, the `figure` environment automatically numbered the images within the document.

The `figure` environment starts with `\begin{figure}` and ends with `\end{figure}` command.

- **Positioning the Images:** The following command will make use of the `figure` environment to place the figure as floating-point. Additionally, we can use the `\centering` command to align the image in the center of the document (default is left align).

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

- **Adding Captions:** Captions can be added to briefly describe the images using the `\caption` command. The position of the caption, below or above the image, is determined by the placement of `\caption` command. If the `\caption` command is placed before the `\\includegraphics` command, the caption will appear above the image and vice versa.

  ```
     \begin{figure}[h]
        \centering
        \includegraphics[width=\textwidth]{latex-logo}
        \caption{This is LaTeX project logo}
     \end{figure}
  ```

- **Adding Labels:** Labels are useful for cross-referencing the images in the document. A label can be added to the image by using the `\label` command and then use that label to refer the image in the document.

  ```
     \begin{figure}[h]
        \centering
        \includegraphics[width=\textwidth]{latex-logo}
        \caption{This is \LaTeX\ project logo}
        \label{logo}
     \end{figure}

     The figure \ref{logo} show the \LaTeX\ project logo on page \pageref{logo}.
  ```

  `\ref` command refers to the image and `\pageref` command prints the page number where the referred image is placed.

Note: you may need to click the run button twice to print the page numbers in the document.

- **List of Figures:** Finally, we can generate a list of figures by using the `\listoffigures` commands after the `\begindocument`.

#### Adding Multiple Images

We can add multiple images to the adding by using a combination of `subcaption` package and `subfigure` environment.

Let's add `subcaption` package in the preamble of the `.tex` file and define `subfigure` environment within the `figure` environment.

```
   \begin{document}

   \begin{figure}[h!]
      \centering
      \begin{subfigure}[b]{0.4\linewidth}
         \includegraphics[width=\linewidth]{latex-logo}
         \caption{\LaTeX\ logo}
         \label{logo1}
      \end{subfigure}
      \hfill
      \begin{subfigure}[b]{0.4\linewidth}
         \includegraphics[width=\linewidth]{latex-logo}
         \caption{Same \LaTeX\ logo}
         \label{logo2}
      \end{subfigure}

      \caption{\LaTeX\ logo}
      \label{logo3}

   \end{figure}

   We have added figures \ref{logo1} and \ref{logo2} in the figure \ref{logo3} on page \pageref{logo3}.

   \end{document}
```

In the above block of code:

- We first defined the `figure` environment and then `subfigure` environment inside it
- For the `subfigure` environment, `[b]` is placement specifier and `{0.4\linewidth}` is the width of the image box (not the width of the image itself). The Sum of widths for all image boxes must be less than the linewidth if we want to have all images in one line. For example, if we want to put three images in one line, we can set the image box width as `0.3\linewidth`.
- In `\includegraphics[width=\linewidth]{latex-logo}`, we specify image width and path. Here the `linewidth` is the width we have specified in the `\begin{subfigure}[b]{0.4\linewidth}`. In other words, if we use `width=\linewidth` in `\includegraphics` command, it will use all the width specified in the `subfigure` command.
- We can add some space between the images using horizontal fill `\hfill` command.
- Additionally, we can assign caption and label to each image using `\caption` and `\label` commands respectively for cross-referencing.

#### Wrapping Text around the Image

We can wrap text around the images especially in the case when there are multiple small images in the document. To achieve this, we will make use of another environment called `wrapfigure`. Let's have a look at the following block of code to wrap the text around the images.

```
 \begin{wrapfigure}{r}{0.48\textwidth}
     \centering
     \includegraphics[width=0.4\textwidth]{latex-logo}
     \caption{\LaTeX\ logo}
     \label{logo4}
 \end{wrapfigure}

 We can wrap text around the images especially in the case when there are multiple small images in the document. To achieve this, we will make use of another environment called 'wrapfigure'. Let's have a look at the following block of code to wrap the text around the images.

 \begin{wrapfigure}{l}{0.48\textwidth}
     \centering
     \includegraphics[width=0.4\textwidth]{latex-logo}
     \caption{\LaTeX\ logo}
     \label{logo5}
 \end{wrapfigure}

Other placement specifiers that can be used are 'l', 'i', and 'o' which will place the images left to the text, inside the edge, and outside the edge respectively.
```

In the above block of code:

- In `\begin{wrapfigure}{r}{0.4\textwidth}`, `{r}` is the placement specifier that will place the image to the right of the text.

- Other placement specifiers that can be used are `l`, `i`, and `o` which will place the images left to the text, inside the edge, and outside the edge respectively.

- The image width is slightly less than the width of the image box to add some white space between image and text.

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

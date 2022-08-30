# Documentation with <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> {#ch3}

In this chapter: 

- What is <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> and why use it? 

- Let's make this simple: Using Overleaf to create <span class="latex">T<sub>E</sub>X</span>-style documents 

- Working with templates

- Conventions in <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> 

Portions of this chapter were derived from [Learn LaTeX in 30 minutes](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes#Writing_your_first_piece_of_LaTeX) available on Overleaf--please check out this resource! 

## <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span>: It's pronounced LAH-tekh or LAY-tekh

<span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> is a document preparation program that allows you to easily develop documents in plain text that are later compiled into PDF form. Most word processors follow a "What You See Is What You Get" preparation-- the page you see typed is the final product. <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> instead uses an underlying computational software to turn the typed plain text into a user-specified style output that can easily be changed to conform to your desired specifications, or those of academic journals. With <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span>, formatting tables, writing equations, and auto-formatting section and figure labels becomes a breeze. What this all means will become more clear as we explore further. 

There are many distributions that will help you navigate the creation of <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> documents, including even some features in R. However, online programs are becoming more useful and transportable means to navigate the <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> environment. So, instead of asking you to download any software, we'll instead direct you to go to [Overleaf](https://www.overleaf.com/), an online TeX editor that is also a collaborative environment. Overleaf makes it easy to see document history, discover templates for specific document types (e.g. CVs or posters) or journal submission requirements, and access your projects from many different machines without having to download <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> on each of them. 

Throughout this course, and likely others, you will use <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> to format and compile your homework assignments. In many cases, your homework problems are already typeset into a <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> document, all that you will be required to do is format the answers in the same document and compile the document (i.e. convert the document into a PDF) to turn in via email or on Canvas. 

In the case that you would instead like to explore a software option for <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> on your home computer, you can check out [TinyTeX](https://yihui.org/tinytex/). 

### Getting Set Up on Overleaf 

To get started, you will need to create an [Overleaf account](https://www.overleaf.com/register). This is straightforward. A premium plan is likely not necessary right now, though you might consider looking into the more advanced plans later. The premium student plan is available for only $8/month. 

Once you have created your account and logged in, you will encounter your main page. One day it will be filled with all of your works in progress, but for today it should look something like this: 

![Overleaf Demo](overleaf-demo.png){width=90%}


As you can see, this site is pretty easy to navigate and we'll leave it up to you to explore a little bit. 


## Your First <span class="latex">L<sup>A</sup>T<sub>E</sub>X</span> Overleaf Project 

To get started, choose the **New Project** button in green on the left-hand side of the page. In the drop-down menu, choose "Example Project" and name the project something like "2022_Tutorial_LASTNAME". 

Once you select **Create**, the new project will open. On this project page, the far left-hand side is a file tree of all the images, .tex files, or other necessary components needed to compile the final document (this will make sense, we promise!!). 

The middle pane is your plain text file. At start-up, this file will be named "main.tex"-- all plain text files that you want to render in a pdf end in ".tex". The "main.tex" file is where you will want to input all of the text that you wish to publish for this particular document. 

![Overleaf Main .tex File](overleaf-main.png){width=100%}


The right-hand pane is a preview of your rendered document given the formatting specifications given in "main.tex".  

![Overleaf Compiled File](overleaf-final.png){width=100%}


This example document provided by Overleaf will go a long way in showing you the intricacies of preparing a TeX-style document. Here, we'll go over some of the main points to ensure you can at least turn in the first few homework assignments without an issue. 

## The Anatomy of a TeX-style document 

This section will assume that you are still viewing the same tutorial document accessed in the previous section. Here we will discuss a bit about the composite elements of a TeX document required to successfully compile. A compiled TeX file is one that made the journey from plain file to PDF rendered document.

The beginning of every .tex file will start with a **preamble**. The preamble is the section where you specify the document class, details you would like to implement throughout the document, and define the parameters of elements that might appear in the text. The preamble is also important for indicating which packages that you would like LaTeX to use to create certain features of your text. Packages are simply additional code components developed to make certain features more feasible without requiring that users code all the specifications themselves. Different packages are useful for modifying the design and layout of things like tables or sections with multiple column. 

In the tutorial .tex document on Overleaf, the following text composes the preamble, which is not published text. After the preamble, the code `\begin{document}` begins the section of published text. 


```r
\documentclass{article}

% Language setting
% Replace `english' with e.g. `spanish' to change the document language
\usepackage[english]{babel}

% Set page size and margins
% Replace `letterpaper' with `a4paper' for UK/EU standard size
\usepackage[letterpaper,top=2cm,bottom=2cm,left=3cm,right=3cm,marginparwidth=1.75cm]{geometry}

% Useful packages
\usepackage{amsmath}
\usepackage{graphicx}
\usepackage[colorlinks=true, allcolors=blue]{hyperref}

\title{Your Paper}
\author{You}

\begin{document}
```

Two elements of this preamble are absolutely necessary in all cases. The codes `\documentclass{}` and `\begin{document}` are required of all documents. Additionally, `\end{document}` is always required at the end of the text to ensure that the document compiles. The remaining packages are loaded in via the command `\usepackage{}`. We won't cover anything else related to class="latex">L<sup>A</sup>T<sub>E</sub>X</span> packages here, as there are a multitude of them and each has their own documentation 

The text between the commands `\begin{document}` and `\end{document}` is the **body**. The body of the text is exactly as you specify it to be! While this is where you will type all of the relevant text you want to typeset, you will also see the body littered with *commands* and *comments.* Throughout a .tex file a command will always begin with a back slash `\` followed by the chosen command. To ensure that the command runs properly, you will have to ensure that the accompanying package is included in the preamble. For example, if I wanted to typeset a table with a caption I would specify the command `\begin{table}` before the table and formatting text and specify the `\end{table}` at the end, the `\caption{}` command falling somewhere between. 


```r
\begin{table} 

\caption{Here is a table about interesting activities in Chicago}
\begin{tabularx}{|c|c|}
\hline 
Actvity & Neighborhood \\ 
\hline 
WhirlyBall & Logan Square \\
\hline 
Nature Conservatory & Lincoln Park or Garfield Park \\
\hline 
\end{tabularx}

\end{table}
```

You might also want to comment on your code, or put notes as to what certain packages do as in the preamble above. To do so, you simply begin the comment text with a percentage symbol `%`. The comment can begin anywhere in the text that you want and is stopped when a new line of text is started (i.e. you must hit *Return* to end the comment line). 

### Exercise 

1. Change the preamble text in the tutorial document to reflect your authorship and a chosen title. See the commands for `\title{}` and `\author{}`. 

2. Edit the abstract text to describe a few goals you have for this class or your first year of grad school. 

3. Recompile the document and take a look at the right-hand pane of Overleaf. Does the newly compiled document reflect your changes? Or do you get an error? 

## Adding dimension to a base document 

Given the above section, you should be able to make sense of the basic elements necessary to compile a TeX document into a PDF. Beyond these necessities, there are a lot of ways to play around with the text to make it more readable and interesting, or to input relevant figures to the text. The tutorial document walks you through many of these issues, such as creating sections, adding figures and tables, lists, and equations. You should walk through each of these sections to ensure that you have an even better grasp of <class="latex">L<sup>A</sup>T<sub>E</sub>X</span>. For now, skip the section on citations and references (2.9), but you will *definitely* want to come back to this later given Overleaf's integration with Zotero and Mendeley. 

There are a couple of things that the Overleaf Tutorial did leave out about altering text that are worth mentioning here. 

1) Bold or italic text is included via the commands `\textbf{*text here*}` and `\textit{*text here*}`, respectively. Further examples are available regarding text features like that in [this Overleaf documentation](https://www.overleaf.com/learn/latex/Bold%2C_italics_and_underlining). 

2) Moving from typical text processing software to TeX document preparation can be difficult because you can't always coerce the spacing that you want. Skipping lines does not equate to creating spacing in the resulting PDF. Instead we have to coerce spacing via different commands. To coerce vertical space, you can use the command `\vspace{}` with the desired amount of spacing and a unit of measurement. The same can be done to tab spacing, or create horizontal space, via the command `\hspace{}`. You can also coerce a line break with `\\` at the point where you desire the line break. 

3) Related to (2), paragraph indenting is not as simple as tabbing as in Word or another word processor. Instead, you can specify this via a command in the document related to indentation for the entire document `\setlength{\parindent}{}`. The argument for this command should specify the length of the desired indent in the points or `pt`. More [here](https://www.overleaf.com/learn/latex/Paragraphs_and_new_lines#Paragraph_indentation). 

4. In an equation environment, you cannot use regular text without breaking the equation. If you want to use text in an equation environment without closing off the equation first, you can use the command `\text{}` with the desired regular text. 

### Exercise 

1. Start a new section at the end of the tutorial document that you name **Tutorial Workspace**. 

2. In your new Tutorial Workspace, create a numbered list of skills that you would like to learn by the end of Math Camp. List them in the order of your priority. 

3. Using an unnumbered list environment, create a list of supplies that you think might make grad school better. They can be real or imaginary supplies. 

4. Create a paragraph where you describe the things that you have learned in Math Camp so far in **bold** characters. Write a couple sentences about what you are excited about in *italics*. 

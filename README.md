# Introduction

This repository is meant to be used as a template for writing research papers using pandoc and markdown. It's the solution I've found so far that I like best as an alternative to WYSIWYG solutions like Word. LaTeX is overly complicated, and solutions like RMarkdown/Bookdown are basically just this solution with more requirements to get up and running (although they have some features that some people might find useful).

The paper.md file is the actual template document, while the output.* files show how it renders in different formats.

# Instructions

### Required software

##### Pandoc

Pandoc is a tool for converting files from one format to another. In this case we use it to turn markdown files to pdf or html files. Instructions for installing pandoc: https://pandoc.org/installing.html

##### LaTeX

In order for pandoc to convert your document to a pdf, it needs LaTeX installed on your computer. Different operating systems have different options for installing LaTex. Fortunately, the pandoc installation guide given previously has recommendations for each operating system (MiKTeX for Windows, BasicTeX or TinyTeX for MacOS, and TeX Live for Linux).

##### Python and pip

Python is needed to install some of the pandoc filters used by this template. pip is just a tool for downloading python packages, and should be included with python.

##### Filters

In order for pandoc to do special things to the document, like automatically number figures and equations, and automatically format citations and bibliographies, pandoc uses filters to modify the document.

The *pandoc-citeproc* filter formats the citations and bibliography so you don't have to. It may or may not be automatically included with pandoc, depending on how it was installed.

The *pandoc-fignos* filter automatically numbers figures. It's a python package, so to install using pip:

```
pip install pandoc-fignos
```

The *pandoc-eqnos* filter automatically numbers equations. It's a python package, so to install using pip:
```
pip install pandoc-eqnos
```

### Writing the documentclass

*TODO: details about line numbers, citations, cross references, etc*

### Generating the output

##### pdf

To create the pdf, use the following command:

```
pandoc paper.md -o out/output.pdf --filter=pandoc-fignos --filter=pandoc-eqnos --filter=pandoc-citeproc
```

If all works well, you should get a pdf document in the *out/* folder.

##### HTML

To create the html, use the following command:

```
pandoc paper.md -s -o out/output.html --filter=pandoc-fignos --filter=pandoc-eqnos --filter=pandoc-citeproc --mathjax
```

If all works well, you should get a html document in the *out/* folder.

*NOTE: Currently, the abstract is not included in the html output. I haven't take the time yet to figure out why or come up with a solution.*

# Useful Links

http://arthurcgusmao.com/academia/2018/01/27/markdown-pandoc.html

https://ctan.org/pkg/psnfss

https://github.com/tomduck/pandoc-fignos#installation

https://blog.kdheepak.com/writing-papers-with-markdown.html

https://stackoverflow.com/questions/25042901/how-to-use-latex-equation-environment-in-pandoc-markdown

https://tex.stackexchange.com/questions/111868/pandoc-how-can-i-get-numbered-latex-equations-to-show-up-in-both-pdf-and-html-o

https://github.com/jgm/pandoc/issues/3148

# Old stuff. Ignore.

pandoc paper.md -o out/output.pdf --filter=pandoc-fignos --filter=pandoc-eqnos --filter=pandoc-citeproc

--number-sections

pandoc paper.md -s -o out/output.html --filter=pandoc-fignos --filter=pandoc-eqnos --filter=pandoc-citeproc --mathjax

pandoc paper.md -s -o output.html --filter=pandoc-fignos --filter=pandoc-eqnos --filter=pandoc-citeproc --filter=pandoc-crossref

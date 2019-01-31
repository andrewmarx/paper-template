# Introduction

This repository is meant to be used as a template for writing research papers using pandoc and markdown. It's the solution I've found so far that I like best as an alternative to WYSIWYG solutions like Word. LaTeX is overly complicated, and solutions like RMarkdown/Bookdown are basically just this solution with more requirements to get up and running (although they have some features that some people might find useful).

It is important to realize that this approach will not necessarily format everything the way you would want for a final printable document. Instead, it is meant more for improving the writing process itself by automatically providing a document that is formatted to resemble a manuscript. Then once the content of the paper is finished, other tools will likely be needed to perform/tweak the final formatting to produce the final document.

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

### File overview

### Writing the Document

The paper.md template has two distinct sections. The first is the YAML header, which is used to provide data about the document. This includes things like the title, author(s), basic formatting, locations of useful files, etc. The rest of the template is markdown, and is where all of the actual written content of the paper is located.

##### YAML header

The YAML header starts and ends with three hyphens `---`

The first part of the YAML should be fairly self explanatory; it provides the title, abstract, and a list of authors

```
title: "Really Cool Title"
abstract: "A mind-blowing abstract."
author:
- First Name
- Second Name
- Third Name
```

The second part provides information needed for automatically formatting the references and citations

```
bibliography:
    - ./res/bib/bibliography.bib
csl: ./res/csl/ecology.csl
link-citations: true
```

The `bibliography:` option allows users to define one or more bibtex files that contain information about the papers that will be cited. Any reference manager should be able to export bibtex files for you. Papers that are not cited by the document do not need to be removed from the bibtex file; pandoc will only put cited papers in the references section.

The `csl:` option provides a link to a csl file, which contains the actual information for formatting citations. In this case, the template document uses formatting guidlines from the journal Ecology. To use the format of another journal, just replace it with the csl file for another journal. The best place to begin looking for specific csl files is here: https://citationstyles.org/authors/

##### Markdown Content

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

*NOTE: Currently, the abstract and line numbers are not included in the html output.*

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

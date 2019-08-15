# Introduction

This repository is meant to be used as a template for writing research papers using pandoc and markdown. It's the solution I've found so far that I like best as an alternative to WYSIWYG solutions like Word. LaTeX is overly complicated, and solutions like RMarkdown/Bookdown are basically just this solution with more requirements to get up and running (although they have some features that some people might find useful).

It is important to realize that this approach will not necessarily format everything the way you would want for a final printable document. Instead, it is meant more for improving the writing process by providing a document that is automatically formatted to resemble a manuscript. Then once the content of the paper is finished, other tools will likely be needed to cleanup the final formatting.

# Instructions

## Required software

### Pandoc

Pandoc is a tool for converting files from one format to another. In this case we use it to turn markdown files to pdf or html files. Instructions for installing pandoc: https://pandoc.org/installing.html

### LaTeX

In order for pandoc to convert your document to a pdf, it needs LaTeX installed on your computer. Different operating systems have different options for installing LaTex. Fortunately, the pandoc installation guide given previously has recommendations for each operating system (MiKTeX for Windows, BasicTeX or TinyTeX for MacOS, and TeX Live for Linux).

### Python and pip

Python is needed to install some of the pandoc filters used by this template. pip is just a tool for downloading python packages, and should be included with python.

### Filters

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

## File overview

## Writing the Document

The examples have two distinct sections. The first is the YAML header, which is used to provide data about the document. This includes things like the title, author(s), basic formatting, locations of useful files, etc. The rest of the examples is markdown, and is where all of the written content of the paper is located.

### YAML header

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

### Markdown Content

There are numerous guides available for learning markdown (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet is a good one). Although the fundamentals are the same, be aware that there are some variants of markdown with special features that might not work using the setup here.

#### Citations

One of the coolest features of using this setup is the way citations are automatically handled. To create citations, you use the article keys in the bibtex file. These keys are unique identifies for each of your papers. Generally, your reference manager should be providing them for you, commonly in a format that includes the first authors last name followed by the year of publication, which usually makes it easy to guess them. In the case of the example bibliography included in this template, the key is *Waples2015*. There are cases where the key might not follow this exact format, such as when you have two papers from the same year by the same author. In this case, the reference manager will modify one or both to make them unique. You can also edit the keys manually, if you wish. Ultimately, you just have to be careful about double checking the citations in the produced document.

Once you know the key, you perform citations one of two ways. The first is parenthetical, which is done using square brackets: `Test citation [@Waples2015].` which produces `Test citation (Waples and Allendorf 2015).` in the final document.

The second way to perform a citation is without the square brackets: `Second test citation by @Waples2015.` which produces `Second test citation by Waples and Allendorf (2015).` in the final document.

At the end of the document, the full citation is automatically inserted in the proper order: `Waples, R. S., and F. Allendorf. 2015. Testing for hardy-weinberg proportions: Have we lost the plot? Journal of Heredity 106:1–19.`

And everything is formatted automatically for the journal Ecology using the csl file specified.

Where this design becomes especially useful is when you are submitting manuscripts for different journals with different citation formats. All you have to do is specify a different csl file and run the command to produce the document. You should never have to format citations manually.

#### Math

Using LaTeX is a very powerful way to get very nice looking, consistently formatted mathematical symbols and equations. Here is a good introductory post on the topic: https://meta.stackexchange.com/questions/68388/there-should-be-universal-latex-mathjax-guide-for-sites-supporting-it/70559#70559

To start, you can either embed math inline, or have it produced on its own line. You can then decide which math blocks have an equation number assigned to it (with the actual numbers determined automatically). Finally, you can make references to numbered equations (again, with the number part being produced automatically).

#### Figure numbering and cross-reference

See: https://github.com/tomduck/pandoc-fignos

To mark a figure for numbering, add an identifier to its attributes:

```
![Caption.](image.png){#fig:id}
```

Alternatively, use reference link attributes. The prefix #fig: is required. id should be replaced with a unique string composed of letters, numbers, dashes and underscores. If id is omitted then the figure will be numbered but unreferenceable.

To reference the figure, use
```
@fig:id
```

#### Table numbering and cross-reference

See: https://github.com/tomduck/pandoc-tablenos

To mark a table for numbering, add an id to its attributes:
```
A B
- -
0 1

Table: Caption. {#tbl:id}
```
The prefix #tbl: is required. id should be replaced with a unique identifier composed of letters, numbers, dashes and underscores. If id is omitted then the figure will be numbered but unreferenceable.

To reference the table, use
```
@tbl:id
```

#### Equation numbering and cross-reference

See: https://github.com/tomduck/pandoc-eqnos

To mark an equation for numbering, add an identifier to its attributes:

```
$$ y = mx + b $$ {#eq:id}
```
The prefix #eq: is required. id should be replaced with a unique string composed of letters, numbers, dashes and underscores. If id is omitted then the equation will be numbered but unreferenceable.

To reference the equation, use

```
@eq:id
```

## Generating the output

### pdf

To create the pdf, use the following command:

```
pandoc example1.md -o out/example1.pdf --filter=pandoc-fignos --filter=pandoc-eqnos --filter=pandoc-tablenos --filter=pandoc-citeproc
```

If all works well, you should get a pdf document in the *out/* folder.

### HTML

To create the html, use the following command:

```
pandoc example1.md -s -o out/example1.html --filter=pandoc-fignos --filter=pandoc-eqnos --filter pandoc-tablenos --filter=pandoc-citeproc --mathjax
```

If all works well, you should get a html document in the *out/* folder.

*NOTE: The abstract and line numbers are not included in the html output.*

### DOCX

To create the docx (doc is also available but with less customization), use the following command:

```
pandoc example1.md -s -o out/example1.docx --filter=pandoc-fignos --filter=pandoc-eqnos --filter pandoc-tablenos --filter=pandoc-citeproc --mathjax
```

If all works well, you should get a docx document in the *out/* folder.


*NOTE: Line numbers are not included in the docx output and must be enabled in Word.*

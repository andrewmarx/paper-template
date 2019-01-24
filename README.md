This repository is meant to be used as a template for writing research papers using pandoc and markdown. It's the solution I've found so far that I like best as an alternative to WYSIWYG solutions like Word. LaTeX is overly complicated, and solutions like RMarkdown/Bookdown are basically just this solution with more requirements to get up and running (although they have some features that some people might find useful).

The paper.md file is the actual template document, while the output.pdf file shows how it renders.

The following is an unorganized list of links and what not that I've found useful and need to incorporate more fully into this README

http://arthurcgusmao.com/academia/2018/01/27/markdown-pandoc.html

https://ctan.org/pkg/psnfss

https://github.com/tomduck/pandoc-fignos#installation

https://blog.kdheepak.com/writing-papers-with-markdown.html

https://stackoverflow.com/questions/25042901/how-to-use-latex-equation-environment-in-pandoc-markdown

pandoc paper.md -o output.pdf --filter=pandoc-fignos --filter=pandoc-eqnos --filter=pandoc-citeproc --number-sections

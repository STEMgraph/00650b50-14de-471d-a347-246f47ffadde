<!---
{
  "id": "00650b50-14de-471d-a347-246f47ffadde",
  "teaches": "Compiling Your First LaTeX Document",
  "depends_on": ["2c7334b3-b07d-48d6-a562-79072d8e166e"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-15",
  "keywords": ["LaTeX", "compilation", "documentclass", "vim", "wymiwyg"]
}
--->

# Compiling Your First LaTeX Document

> In this exercise you will learn how to compile your first LaTeX document using a terminal-based workflow. Furthermore we will explore how to structure documents with sections, subsections, and chapters by using various LaTeX document classes.

### Introduction

LaTeX is a powerful document preparation system that enables precise control over structure, formatting, and content presentation. Unlike word processors, which emphasize what-you-see-is-what-you-get (WYSIWYG), LaTeX is a markup language where you describe what content means and how it should behave (what-you-mean-is-what-you-get, or WYMiwyg). This distinction makes LaTeX particularly suited for producing complex documents such as theses, scientific papers, or technical documentation.

LaTeX was originally developed by Leslie Lamport in the 1980s as a set of macros built on top of TeX, a typesetting system created by Donald E. Knuth. Knuth, a professor of computer science at Stanford University, began developing TeX in 1977 out of frustration with the declining quality of mathematical typography in published works. His goal was to provide a high-quality, programmable typesetting system that could meet the exacting standards of mathematical and scientific publications. Knuth’s work on TeX was part of a broader movement to reclaim typographic precision, and he remains an influential figure in both theoretical computer science and the field of digital typography.

TeX, although still the foundation of LaTeX, is rarely used directly today except in very specific or legacy workflows. LaTeX has effectively supplanted TeX in most practical settings due to its higher-level abstraction and ease of use. When you compile a LaTeX document, you are in fact compiling TeX code under the hood. The LaTeX compiler translates your LaTeX source into TeX commands, which are then processed into a device-independent (DVI) or PDF file.

The steps typically involve:
1. Parsing the LaTeX source and macros.
2. Generating an intermediate representation (DVI or directly to PDF).
3. Resolving references, table of contents, and figures through multiple passes.

This might sound technical, but it's similar in principle to how WYSIWYG editors like Microsoft Word function: even in Word, every paragraph, font, style, and heading level has associated metadata. These programs store such metadata invisibly, creating a binary document that a user edits visually. In contrast, LaTeX makes this metadata explicit and editable in plain text.

This visibility is LaTeX’s greatest strength — you work directly on the source code of what would otherwise be hidden formatting instructions in a WYSIWYG system. While it demands more awareness and responsibility from the author, it also grants greater precision, repeatability, and control. Understanding that all text processors, even graphical ones, operate on structured content allows you to appreciate the transparency and flexibility LaTeX provides.

In this exercise, you’ll work with LaTeX in a command-line environment using Vim, a modal text editor. You'll start by installing the appropriate LaTeX compiler for your operating system. Then, you'll write a minimal LaTeX document and progressively introduce structural components like sections, chapters, and parts. The final objective is to understand how document classes in LaTeX determine which structures are available and how documents are rendered.

Whether you plan to work in academia or industry, mastering LaTeX or at least the idea behind it offers an efficient, reproducible, and automation-friendly approach to documentation.

### Further Readings and Other Sources
- [LaTeX Project - Official Site](https://www.latex-project.org/)
- [Overleaf's Introduction to LaTeX](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
- [YouTube - LaTeX Tutorial by Michelle Krummel](https://www.youtube.com/watch?v=VhmkLrOjLsw)
- [The Not So Short Introduction to LaTeX](https://tobi.oetiker.ch/lshort/lshort.pdf)

---

## Tasks

### Task 0: Installing the LaTeX Compiler

To compile LaTeX documents locally, you need to install a TeX distribution. Follow the instructions according to your operating system:

#### Linux
```bash
sudo apt update
sudo apt install texlive-full
```

#### Windows
1. Download and install [MiKTeX](https://miktex.org/download).
2. During installation, ensure the option to install missing packages on-the-fly is enabled.

#### macOS
Install MacTeX using Homebrew:
```bash
brew install --cask mactex
```
Alternatively, download from [https://tug.org/mactex/](https://tug.org/mactex/).

### Task 1: Writing a Minimal LaTeX Document in Vim

This task introduces the minimal elements of a LaTeX document. You will create a simple file, write LaTeX markup, and compile it to PDF. 

1. Open Vim and create a new file:
```bash
vim hello.tex
```
2. Enter Insert mode (`i`) and type the following LaTeX code:
```latex
\documentclass{article}
\begin{document}
Hello, world!
\end{document}
```
3. Press `Esc`, then type `:wq` to save and exit.
4. Compile the document with:
```bash
pdflatex hello.tex
```
5. This generates `hello.pdf` — open it with any PDF viewer to verify the result.

This simple file includes the document class, the document body, and your first text output. Understanding this basic layout is essential before adding complexity.

### Task 2: Adding Structure with Sections and Subsections

LaTeX excels at structured documents. In this task, you’ll extend your document using headings.

1. Edit your `hello.tex` file or create a new one:
```latex
\documentclass{article}
\begin{document}

\section{Introduction}
This is the introduction.

\subsection{Motivation}
Here we explain why we write this document.

\subsection{Goals}
We aim to learn LaTeX.

\section{Conclusion}
We have seen how to use sections.

\end{document}
```
2. Save and compile as before:
```bash
pdflatex hello.tex
```
3. You’ll now see a structured output, and LaTeX automatically formats headings and spacing.

Sections and subsections are logical building blocks. LaTeX automatically numbers them and includes them in the Table of Contents if specified.

### Task 3: Exploring Document Classes and Using Chapters

Now you’ll learn how different document classes alter structure. Replace `article` with `book` to access `\chapter` and `\part`:

```latex
\documentclass{book}
\begin{document}

\part{Fundamentals}

\chapter{Introduction}
This is the first chapter.

\section{Background}
Some background information.

\chapter{Advanced Topics}
Details of advanced topics go here.

\end{document}
```

Compile this with `pdflatex`. You'll see:
- A title page generated automatically.
- Chapters starting on new pages.
- Parts dividing the book into large conceptual units.

Understanding document classes helps tailor your formatting and structure. Try also `report`, `memoir`, or `letter` for different use cases.

---

## Questions

1. Why do we use type-set-description languages like LaTeX instead of WYSIWYG tools?
2. How does LaTeX make automation easier, especially in academic or technical workflows?
3. Why is maintaining a consistent style easier with LaTeX?
4. What different `documentclass` options are available, and where can one find more?

---

## Advice

Learning LaTeX isn’t just about mastering a specific tool; it’s about grasping a larger concept — that of "what-you-mean-is-what-you-get" (WYMiwyg). In engineering and technical fields, where documents need to be maintainable, reproducible, and often generated or updated programmatically, WYMiwyg principles become invaluable. Tools may change — Markdown, reStructuredText, AsciiDoc — but the idea of separating content from presentation remains crucial. Understanding LaTeX provides a solid foundation for navigating this landscape and will benefit you greatly as you move into more complex documentation or collaborative projects. Don’t get stuck on LaTeX’s syntax — focus on the clarity and structure it enforces.


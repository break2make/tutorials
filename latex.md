Latex
---

# Useful latex package

## \usepackage{tasks}

Latex [wiki](https://en.wikibooks.org/wiki/LaTeX/List_Structures) has summarized various useful packages for list. The `tasks` package is useful to create horizontal list which is required when you are preparing a question with multiple choices for answer. Try this example from Latex [wiki](https://en.wikibooks.org/wiki/LaTeX/List_Structures):
```
\documentclass[12pt]{article}
\usepackage{tasks}
\usepackage{exsheets}
\SetupExSheets[question]{type=exam}
\begin{document}
\begin{question}
	Which one of the entries does not fit with the others?
	\begin{tasks}(4)
		\task mercury
		\task iron
		\task lead
		\task zinc
	\end{tasks}
\end{question}
\settasks{
	counter-format=(tsk[r]),
	label-width=4ex
}
\begin{question}
	What is a funkyton?
	\begin{tasks}(2)
		\task A dancing electron
		\task A dancing proton
		\task A dancing neutron
		\task A Dixie Dancing Duck
	\end{tasks}
\end{question}
\end{document}
```

# \usepackage{enumitem}

To define a custom list, check this [post](https://tex.stackexchange.com/questions/186888/newlist-vs-newenvironment-for-defining-an-individual-list-style). In addition, check this [post](https://texblog.org/2011/10/10/increase-enumerate-itemize-depth-with-enumitem/) to define a multi-level list.

# \usepackage[most]{tcolorbox}
This is useful to have beautiful color box area. Check the official [manual](http://ctan.math.washington.edu/tex-archive/macros/latex/contrib/tcolorbox/tcolorbox.pdf) for usage.

# Create PDF Form
For creating a fillable pdf form, please the [book][book-latex-Kottwitz] by Stefan Kottwitz and this [link](https://texwelt.de/fragen/7768/wie-erstelle-ich-ein-gutes-ausfullbares-pdf-formular#).

[book-latex-Kottwitz]: https://books.google.co.in/books?id=PPx_CwAAQBAJ&pg=PA214&lpg=PA214&dq=hyperref+with+java+script+support+in+latex&source=bl&ots=f7vLOY73jZ&sig=ACfU3U1LdU1d-MyV7TLB4GvpHkBeUclTYQ&hl=en&sa=X&ved=2ahUKEwiZkJSxzoDpAhXl7nMBHQ7XDbIQ6AEwBXoECA0QAQ#v=onepage&q=hyperref%20with%20java%20script%20support%20in%20latex&f=false


# How to pass option to a package
I came across a situation where `enumitem` package was loaded as a part of class file with certain options, and I wanted to add `inline` option as \usepackage[inline]{enumitem}. However, it produced error as "option clash". To get more details on option clash, check [here](http://www.texfaq.org/FAQ-optionclash). 
After a search, I found this stackexchange [post](https://tex.stackexchange.com/questions/379793/inline-option-for-enumitem), which save my hours.

You have a couple of options to resolve the issue:
- You could use `\PassOptionsToPackage` as: 
    ```
    \PassOptionsToPackage{inline}{enumitem}
    \documentclass{mdpi}
    ```
- You could pass the inline option to the documentclass ``\documentclass[inline]{mdpi}``. However, I have not tried this.

# Don't use these packages together

## Packages: enumitem and paralist

Personally, I like the `paralist` for inline list within a paragraph. But there was conflict when it is used with `enumitem` package. Although it might work for few document classes, but not compatible for each documentclass. Now, I have decided to avoid using `paralist` and want to use `enumitem` with as:
- Load `\usepackage[inline]{enumitem}`
- Use started version of enumerate environment as:
    ```
    \begin{enumerate*}[label=(\alph*)]
    \item A
    \item B
    \end{enumerate*}
    ```
    Change the `\label` as it is required for your writing. But this approach leaves additional spaces, which I do not like. We need additional settings to adjust the space.

# References
- [LaTeX Cookbook By Stefan Kottwitz][book-latex-Kottwitz]
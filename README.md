# Fondamenti di Automatica

This is a partial collection of theory and exercises from a course on the Fundamentals of Automation (Fondamenti di Automatica) that I took during my Bachelor's Degree in Electronic & Computer Engineering at the University of Ferrara.

- [Introduction](./introduzione.md)
- [Modeling of Dynamic Systems](./modellazione-di-sistemi-dinamici.md)
- [Analysis of Dynamic Systems](./analisi-di-sistemi-dinamici.md)
- [Transfer Functions](./funzioni-di-trasferimento.md)
- [Evaluation of $e^{At}$](./calcolo-di-exp(At).md)

## Requirements and Usage

Github cannot display correctly all of the syntax that I used inside the markdown files, to compile them to a pdf you will need:

- pandoc
- plantuml
- graphviz
- latex
- a java runtime environment
- the python package `pandoc-plantuml`

To compile a single file:

```bash
pandoc "document.md" -o "document.pdf" --filter pandoc-plantuml --verbose
```

# CV Manuel Caipo (LaTeX)

Requisitos para ejecución local: **MiKTeX** y **Strawberry Perl**.

```powershell
texfot xelatex main.tex
```

```powershell
xelatex -interaction=nonstopmode -file-line-error -halt-on-error main.tex | Select-String '^\S+\.tex:\d+:|^!' -Context 0,3
```

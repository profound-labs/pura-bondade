FILE=book_main

LATEX=lualatex
BIBTEX=bibtex

LATEX_OPTS=-interaction=nonstopmode -halt-on-error -shell-escape

all: document

document: mark
	$(LATEX) $(LATEX_OPTS) $(FILE).tex;

mark:
	latex -interaction=nonstopmode -halt-on-error mark.tex
	dvips mark.dvi
	ps2pdf mark.ps
	pdfcrop mark.pdf

view:
	evince $(FILE).pdf &

cover-front:
	$(LATEX) $(LATEX_OPTS) cover_front.tex

cover-back:
	$(LATEX) $(LATEX_OPTS) cover_back.tex

cover-spine:
	$(LATEX) $(LATEX_OPTS) cover_spine.tex
	+pdftk cover_spine.pdf cat 1-endR output cover_spine_R.pdf

cover:
	$(LATEX) $(LATEX_OPTS) cover.tex

cover-all:
	make cover-front
	make cover-back
	make cover-spine
	make cover

clean:
	+rm -fv $(FILE).{dvi,ps,pdf,aux,log,bbl,blg}


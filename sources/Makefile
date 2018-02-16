files  = $(wildcard *.tex)

pdfs = $(files:%tex=%pdf)

handouts = $(pdfs:%=ceng242-%)

slides = $(pdfs:%=ceng242-sl-%)


all: $(slides) $(handouts)

install: all
	cp $(slides) ../slides/ ;\
	cp $(handouts) ../handouts/

ceng242-%.pdf : %.tex
	-pdflatex -jobname=$(@:%.pdf=%) '\documentclass[handout,compress,xcolor=table]{beamer}\input{$<}' && \
	pdflatex -jobname=$(@:%.pdf=%) '\documentclass[handout,compress,xcolor=table]{beamer}\input{$<}'
	
ceng242-sl-%.pdf : %.tex
	-pdflatex -jobname=$(@:%.pdf=%) '\documentclass[slides,compress,xcolor=table]{beamer}\input{$<}' && \
	pdflatex -jobname=$(@:%.pdf=%) '\documentclass[slides,compress,xcolor=table]{beamer}\input{$<}'

clean: auxclean
	-rm $(slides) $(handouts)

auxclean:
	-rm *.aux *.log *.nav *.out *.snm *.vrb *.toc


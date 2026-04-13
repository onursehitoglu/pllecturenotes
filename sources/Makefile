SHELL=/bin/bash

files  = $(wildcard *.tex)

pdfs = $(files:%tex=%pdf)

handouts = $(pdfs:%=../handouts/ceng242-%)

slides = $(pdfs:%=../slides/ceng242-sl-%)


all: $(slides) $(handouts)

#install: all
#	rsync -av $(slides) ../slides/ ;\
#	rsync -av $(handouts) ../handouts/

../handouts/ceng242-%.pdf : %.tex
	-xelatex -jobname=$(@:../handouts/%.pdf=%) '\documentclass[handout,compress,xcolor=table]{beamer}\input{$<}' && \
	xelatex -jobname=$(@:../handouts/%.pdf=%) '\documentclass[handout,compress,xcolor=table]{beamer}\input{$<}' && \
	mv $(@:../handouts/%=%) $(@) && \
	rm $(@:../handouts/%.pdf=%).{aux,log,nav,out,snm,vrb,toc}
	
../slides/ceng242-sl-%.pdf : %.tex
	-xelatex -jobname=$(@:../slides/%.pdf=%) '\documentclass[slides,compress,xcolor=table]{beamer}\input{$<}' && \
	xelatex -jobname=$(@:../slides/%.pdf=%) '\documentclass[slides,compress,xcolor=table]{beamer}\input{$<}' && \
	mv $(@:../slides/%=%) $(@) && \
	rm $(@:../slides/%.pdf=%).{aux,log,nav,out,snm,vrb,toc}

clean: auxclean
	#-rm $(slides) $(handouts)

auxclean:
	-rm *.aux *.log *.nav *.out *.snm *.vrb *.toc


# type "make" command in Unix to create asme2e.pdf file 
all:
	latex asme2e
	bibtex asme2e
	latex asme2e
	dvips -o asme2e.ps asme2e
	ps2pdf asme2e.ps paper.pdf
	mkdir -p ../paper
	mv paper.pdf ../paper/

abstract:
	latex abstract
	dvips -o abstract.ps abstract
	ps2pdf abstract.ps abstract.pdf

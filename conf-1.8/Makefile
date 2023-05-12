# type "make" command in Unix to create asme2e.pdf file 
all: clean
	pdflatex asme2e
	bibtex asme2e
	pdflatex asme2e
	#dvips -o asme2e.ps asme2e
	#ps2pdf asme2e.ps paper.pdf
	mkdir -p ../paper
	mv asme2e.pdf ../paper/paper.pdf

abstract:
	latex abstract
	dvips -o abstract.ps abstract
	ps2pdf abstract.ps abstract.pdf

clean:
	rm -rf *.pdf *.aux *.bbl *.blg *.dvi *.log *.out *.ps

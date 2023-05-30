###################################################
#
# file: Makefile
#
# @Author:   Iacovos G. Kolokasis
# @Version:  19-05-2023
# @email:    kolokasis@ics.forth.gr
#
# Makefile
#
####################################################

PAPER = paper
TEXMK=latexmk
TEX = $(wildcard *.tex)
BIB = paper.bib
FIGS = $(wildcard fig/*.pdf)

.PHONY: all clean

all: $(PAPER).pdf

# -pdf tells latexmk to generate PDF directly (instead of DVI).
# -pdflatex="" tells latexmk to call a specific backend with specific options.
# -use-make tells latexmk to call make for generating missing files.

# -interactive=nonstopmode keeps the pdflatex backend from stopping at a
# missing file reference and interactively asking you for an alternative.
$(PAPER).pdf: $(TEX) $(BIB) $(FIGS)
	-$(TEXMK) -f -interaction=nonstopmode -pdf -use-make $(PAPER).tex

view:
	@(evince $(PAPER).pdf 2> /dev/null & echo $$! > evince.pid)

commit: 
	-git status
ifeq ($(m),)
	-git commit -a -m "Commit all changes"
else
	git commit -a -m "$m"
endif
	git push

up: update

update:
	-git status
	git pull

status:
	git status

lastdiff2:
	-git diff --name-status HEAD HEAD~2

lastdiff:
	-git diff --name-status HEAD HEAD~1

aspell:
	aspell --lang=en --mode=tex check $f

plot:
	-cd raw/scripts && ./run_all.sh 0 && cd -

tag:
	-git tag $m
	-git push origin --tags

cc: clean commit

# Use -bibtex to clean the paper.bbl
distclean:
	-$(TEXMK) -bibtex -C

clean:
	-$(TEXMK) -bibtex -c

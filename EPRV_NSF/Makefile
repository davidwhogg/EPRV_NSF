LATEX       = pdflatex
BASH        = bash -c
ECHO        = echo
RM          = rm -rf
TMP_SUFFS   = aux blg log dvi eps out
CHECK_RERUN = grep Rerun $*.log

all: data.pdf facilities.pdf summary.pdf description.pdf biosketch_hogg.pdf

description.bbl: description.bib description.tex
	${LATEX} description
	bibtex description

description.pdf: description.bbl

%.pdf: %.tex hogg_nsf.tex
	${LATEX} $<
	( ${CHECK_RERUN} && ${LATEX} $< ) || echo "Done."
	( ${CHECK_RERUN} && ${LATEX} $< ) || echo "Done."

clean:
	${RM} $(foreach suff, ${TMP_SUFFS}, *.${suff})

PAPER   = chukan_presentation.tex

FIGURES = 
GRAPHS = 
INPUTS = 

BASE	= $(PAPER:.tex=)
BIB	= $(PAPER:.tex=.bib)
BBL	= $(PAPER:.tex=.bbl)
BLG	= $(PAPER:.tex=.blg)

PSFILES = $(FIGURES:.eps=.ps)
DVI	= $(PAPER:.tex=.dvi)
PS	= $(PAPER:.tex=.ps)
PDF	= $(PAPER:.tex=.pdf)
LOG	= $(PAPER:.tex=.log)
AUX	= $(PAPER:.tex=.aux)

LATEX	= platex
PDFLATEX = pdflatex
BIBTEX	= pbibtex
DVI2PS	= dvips
DVI2PDF	= dvipdfm
PS2PDF  = ps2pdf
PS2EPS	= ps2epsi
PDF2PS	= pdf2ps
GNUPLOT = gnuplot

all: $(PDF) # $(PS)

%.eps : %.ps
	$(PS2EPS) $< $@
%.ps : %.pdf
	$(PDF2PS) $< $@
%.eps : %.dat %.gnuplot
	$(GNUPLOT) $*.gnuplot
%.pic : %.txt
	flow.exe $< $@

$(DVI) : $(PAPER) $(BIB) $(FIGURES) $(GRAPHS) $(INPUTS)
	$(LATEX) $(PAPER) && $(BIBTEX) $(BASE) && $(LATEX) $(PAPER) && while grep "Rerun to get " $(LOG); do $(LATEX) $(PAPER); done

#$(PS) : $(DVI)
#	$(DVI2PS) -t a4 $< -o $@

#$(PDF) : $(PS)
#	$(PS2PDF) $< $@

$(PDF) : $(DVI)
	$(DVI2PDF) -p a4 -o $@ $<

#$(PDF) : $(DVI)
#	$(DVI2PS) -Ppdf -t a4 $< -o $@ 

#$(PDF) : $(PAPER) $(BIB) $(FIGURES) $(GRAPHS)
#	$(PDFLATEX) $(PAPER) && $(BIBTEX) $(BASE) && $(PDFLATEX) $(PAPER) && while grep "Rerun to get " $(LOG); do $(PDFLATEX) $(PAPER); done

clean :
	rm -f $(DVI) $(PDF) $(PS) $(LOG) $(AUX) $(FIGURES) $(GRAPHS) $(PSFILES) $(BBL) $(BLG) *.pbm


#refinementdir = $(includedir)/dune/geometry/refinement

dist_noinst_DATA =								\
	kuhntriangulation.svg kuhntriangulation.png kuhntriangulation.eps	\
	referencetokuhn0.svg referencetokuhn0.png referencetokuhn0.eps		\
	refinement.tex								\
	simplexvertexindex.svg simplexvertexindex.png simplexvertexindex.eps

if BUILD_DOCS
 DOCS = referencetokuhn0.png simplexvertexindex.png
 PDFDOC = refinement.pdf
endif
EXTRAINSTALL = refinement.pdf

docdir=$(datadir)/doc/dune-geometry/refinement
DOCFILES = $(PDFDOC)
EXTRA_DIST = $(PDFDOC) CMakeLists.txt

refinement.dvi: refinement.tex simplexvertexindex.eps referencetokuhn0.eps kuhntriangulation.eps

.svg.eps:
if INKSCAPE
	$(INKSCAPE) --export-dpi=180 -e $@.png $< || { rm -f $@.png ; exit 1; }
if CONVERT
	$(CONVERT) $@.png EPS:$@.tmp || { rm -f $@.tmp ; exit 1; }
else !CONVERT
	echo Sorry, you need convert installed to convert .png into .eps
	exit 1
endif !CONVERT
	mv $@.tmp $@
	rm $@.png
else !INKSCAPE
	echo Sorry, you need inkscape installed to convert .svg into .png
	exit 1
endif !INKSCAPE

MOSTLYCLEANFILES = *.aux *.bbl *.blg *.log *.out *.toc *.dvi *.pdf *.ps *.eps

include $(top_srcdir)/am/latex
include $(top_srcdir)/am/inkscape.am

BASEDIR = ../..
CURDIR = doc/refinement

include $(top_srcdir)/am/webstuff
include $(top_srcdir)/am/global-rules

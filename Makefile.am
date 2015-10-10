## Process this file with automake to produce Makefile.in
bin_PROGRAMS = sng
#bin_SCRIPTS = sng_regress
sng_SOURCES = main.c sngc.c sngd.c sng.h
man_MANS = sng.1
# The man pages and script are here because automake has a bug
EXTRA_DIST = Makefile sng.xml sng.1 sng_regress test.sng 
EXTRA_DIST += snglogo.png control
EXTRA_CLEAN = sng.html

sng.1: sng.xml
	xmlto man sng.xml

sng.html: sng.xml
	xmlto html-nochunks sng.xml

zip: $(DISTFILES)
	zip @PACKAGE@-@VERSION@.zip $(DISTFILES)

# Regression-test sng.  Passes if no differences show up.
# Assumes we have a copy of Willem van Schaik's PNG test suite under pngsuite
regress:
	sng_regress test.sng -s pngsuite/[a-wyz]*.png

release: dist sng.html
	shipper version=$(VERSION) | sh -e -x



MAKEINFO = makeinfo

#MAKEINFOFLAGS = --no-validate
MAKEINFOFLAGS = 

TEXI2DVI = texi2dvi
DVIPS = dvips

all : report.jsh.ps report.si.ps report.cjl1.ps

%.info : %.texi
	$(MAKEINFO) $(MAKEINFOFLAGS) -o $@ $<

%.doc : %.texi
	$(MAKEINFO) $(MAKEINFOFLAGS) --no-headers -o $@ $<

%.dvi : %.texi
	$(TEXI2DVI) $<

%.ps : %.dvi
	$(DVIPS) $<

clean realclean :
	rm -f *~ *.info* *.??? *.??

tar :
	tar cf - `find . '(' -name '*.texi'				\
			     -o -name '[A-Z]*' ')'			\
			  -a '!' -name '*~' -print ` | gzip -c >reports.tgz

nobak :
	rm -f *~

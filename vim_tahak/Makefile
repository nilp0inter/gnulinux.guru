TEX=context

all: Makefile vim_tahak.pdf vim_cheatsheet.pdf vim_cheatsheet_include.html vim_cheatsheet.html vim_cheatsheet_0001.png vim_tahak_include.html vim_tahak.html
		
vim_tahak.pdf: vim_tahak_style.ctex vim_tahak.ctex
	$(TEX) vim_tahak.ctex

vim_cheatsheet.pdf: vim_tahak_style.ctex vim_cheatsheet.ctex
	$(TEX) vim_cheatsheet.ctex

vim_cheatsheet_include.html: vim_cheatsheet.ctex vim_ctext2html.sed
	sed -f vim_ctext2html.sed vim_cheatsheet.ctex > vim_cheatsheet_include.html

vim_cheatsheet.html: vim_cheatsheet_include.html html_header.sed
	sed -f html_header.sed vim_cheatsheet_include.html > vim_cheatsheet.html

vim_tahak_include.html: vim_tahak_style.ctex vim_tahak.ctex vim_ctext2html.sed
	sed -f vim_ctext2html.sed vim_tahak.ctex > vim_tahak_include.html

vim_tahak.html: vim_tahak_include.html html_header.sed 
	sed -f html_header.sed vim_tahak_include.html > vim_tahak.html

vim_cheatsheet_0001.png: vim_cheatsheet.pdf
	pdf2png -x 512 vim_cheatsheet.pdf

.SUFFIXES: .ctex

tarball: vim_cheatsheet.tar.bz2

vim_cheatsheet.tar.bz2: vim_tahak_style.ctex vim_tahak.ctex vim_cheatsheet.ctex
	#$(shell cd ..; tar cvjf vim_cheatsheet.tar.bz2 vim_tahak/)
	cd ..; tar cvjf vim_cheatsheet.tar.bz2 vim_tahak/
#	mv ../vim_cheatsheet.tar.bz2 .

clean:
	rm -f vim*.log

veryclean: clean
	rm -f vim_tahak.pdf vim_cheatsheet.{pdf,html} vim_cheatsheet_include.html vim_cheatsheet_0001.png vim_tahak.html vim_tahak_include.html


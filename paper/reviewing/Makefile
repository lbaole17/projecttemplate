all: repeatedwords tightreferences hardcodednumbers chktex textidote checkURLs

.PHONY: repeatedwords tightreferences hardcodednumbers chktex textidote

repeatedwords:
	egrep "(\b[a-zA-Z]+) \1\b" ../sections/*.tex -n

tightreferences: tightreferences.sh
	bash tightreferences.sh

hardcodednumbers: hardcodednumbers.sh
	bash hardcodednumbers.sh

chktex: ../paper.tex 
	cd .. && chktex paper.tex

textidote: /Applications/textidote.jar ../reviewing/textidote_dico.txt ../paper.tex 
	java -jar /Applications/textidote.jar --check en --dict ../reviewing/textidote_dico.txt ../paper.tex 

URL_LIST:= $(shell grep -o 'href{[A-Za-z0-9:/\._?=]*}' ../sections/*.tex | sed 's/.*href{//' | sed 's/}//' )
checkURLs:
	for URL in $(URL_LIST) ; do wget --spider --no-verbose $${URL} ; done



# from: http://tldp.org/HOWTO/Lex-YACC-HOWTO-4.html
# NOTE: if you get an error about your compiler not being able to find 'yylval', add this to example4.l, just beneath #include <y.tab.h>: 
# extern YYSTYPE yylval;
# This is explained in the 'How Lex and YACC work internally' section.

#LEX=/usr/bin/lex
LEX=/usr/bin/flex
YACC=/usr/bin/yacc

PROG=grammar
TOKENS=tokens
GRAMMAR=grammar

.PHONY:	all
all:	$(PROG) smallclean

$(PROG): $(TOKENS).c $(GRAMMAR).tab.c
	@echo -en " [CC]  "
	cc $(TOKENS).c $(GRAMMAR).tab.c -o $(PROG)



$(TOKENS).c: $(TOKENS).l
	@echo -en " [LEX] "
	$(LEX) -o $(TOKENS).c $(TOKENS).l

$(GRAMMAR).tab.c: $(GRAMMAR).y
	@echo -en " [YAC] "
	yacc -b $(GRAMMAR) -d $(GRAMMAR).y

.PHONY: smallclean
smallclean:
	@echo -en " [SMALLCLEAN] "
	rm -f $(TOKENS).c $(GRAMMAR).tab.c $(GRAMMAR).tab.h

.PHONY: clean
clean:
	@echo -en " [CLEAN] "
	rm -f $(TOKENS).c $(GRAMMAR).tab.c $(GRAMMAR).tab.h $(GRAMMAR).output *.o $(PROG)

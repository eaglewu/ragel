COLM        = @COLM@
COLM_LD     = @COLM_LD@
COLM_LIBDEP = @COLM_LIBDEP@
COLM_BINDEP = @COLM_BINDEP@

bin_PROGRAMS = ragel-js

ragel_js_CPPFLAGS = -I$(top_srcdir)/aapl

dist_ragel_js_SOURCES = main.cc rlhc.c

nodist_ragel_js_SOURCES = \
	rlparse.c rlreduce.cc

ragel_js_LDADD = ../libragel.la ../libfsm.la $(COLM_LD)

BUILT_SOURCES = rlparse.c rlreduce.cc rlhc.c

EXTRA_DIST = rlparse.lm rlhc-js.lm

rlparse.c: rlparse.lm $(COLM_BINDEP)
	$(COLM) -I.. -c -b rl_parse -o $@ -m rlreduce.cc $<

rlreduce.cc: rlparse.c

rlhc.c: rlhc-js.lm
	$(COLM) -I.. -c -b rlhc -o $@ $<

## Process this file with automake to produce Makefile.in

##AUTOMAKE_OPTIONS = no-dependencies

bin_PROGRAMS = mcpp
mcpp_SOURCES = system.H configed.H internal.H \
	main.c control.c eval.c expand.c support.c system.c mbchar.c lib.c
man_MANS = mcpp.1
EXTRA_DIST = $(man_MANS)

if MAINTAINER_MODE

bin_PROGRAMS += mcpp_prestd mcpp_old mcpp_poststd
mcpp_poststd_SOURCES = $(mcpp_SOURCES)
mcpp_poststd_CPPFLAGS = -DMODE=POST_STANDARD
mcpp_prestd_SOURCES = $(mcpp_SOURCES)
mcpp_old_SOURCES = $(mcpp_SOURCES)
mcpp_prestd_CPPFLAGS = -DMODE=PRE_STANDARD
mcpp_old_CPPFLAGS = -DMODE=PRE_STANDARD -DOLD_PREPROCESSOR
install-exec-hook:
	@if test x"$(CC)" = x"gcc"; then \
        ./set_mcpp.sh '$(gcc_path)' $(gcc_maj_ver) '$(cpp_call)' '$(CXX)' 'x$(EXEEXT)' '$(LN_S)'; \
    fi
uninstall-hook:
	@if test x"$(CC)" = x"gcc"; then \
        ./unset_mcpp.sh '$(gcc_path)' $(gcc_maj_ver) '$(cpp_call)' '$(CXX)' 'x$(EXEEXT)'; \
    fi

else

install-exec-hook:
uninstall-hook:

endif


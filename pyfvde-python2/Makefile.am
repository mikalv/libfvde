# Note that we cannot use: AUTOMAKE_OPTIONS = subdir-objects
# subdir-objects will compile the source files to a single version of Python.
# Since subdir-objects is being deprecated we copy the source files instead.
am__installdirs = "$(DESTDIR)$(pyexecdir2)"
pyexecdir = $(pyexecdir2)

if HAVE_PYTHON2
AM_CFLAGS = \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/common \
	@LIBCERROR_CPPFLAGS@ \
	@LIBCDATA_CPPFLAGS@ \
	@LIBCLOCALE_CPPFLAGS@ \
	@LIBCSPLIT_CPPFLAGS@ \
	@LIBUNA_CPPFLAGS@ \
	@LIBCFILE_CPPFLAGS@ \
	@LIBCPATH_CPPFLAGS@ \
	@LIBBFIO_CPPFLAGS@ \
	@LIBFGUID_CPPFLAGS@

am_pyfvde_la_rpath = -rpath $(pyexecdir2)

BUILT_SOURCES = \
	pyfvde.c pyfvde.h \
	pyfvde_datetime.c pyfvde_datetime.h \
	pyfvde_error.c pyfvde_error.h \
	pyfvde_file_object_io_handle.c pyfvde_file_object_io_handle.h \
	pyfvde_guid.c pyfvde_guid.h \
	pyfvde_integer.c pyfvde_integer.h \
	pyfvde_libbfio.h \
	pyfvde_libcerror.h \
	pyfvde_libclocale.h \
	pyfvde_libfguid.h \
	pyfvde_libfvde.h \
	pyfvde_python.h \
	pyfvde_unused.h \
	pyfvde_volume.c pyfvde_volume.h

pyexec_LTLIBRARIES = pyfvde.la

nodist_pyfvde_la_SOURCES = $(BUILT_SOURCES)

pyfvde_la_LIBADD = \
	@LIBCERROR_LIBADD@ \
	../libfvde/libfvde.la \
	@LIBCDATA_LIBADD@ \
	@LIBCLOCALE_LIBADD@ \
	@LIBCSPLIT_LIBADD@ \
	@LIBUNA_LIBADD@ \
	@LIBCFILE_LIBADD@ \
	@LIBCPATH_LIBADD@ \
	@LIBBFIO_LIBADD@ \
	@LIBFGUID_LIBADD@

pyfvde_la_CPPFLAGS = $(PYTHON2_CPPFLAGS)
pyfvde_la_LDFLAGS  = -module -avoid-version $(PYTHON2_LDFLAGS)

$(BUILT_SOURCES):
	/bin/cp -f $(top_srcdir)/pyfvde/$@ $@

endif

MAINTAINERCLEANFILES = \
	Makefile.in

clean-local:
	/bin/rm -f pyfvde*.[ch]

distclean: clean
	/bin/rm -f Makefile


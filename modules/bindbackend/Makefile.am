pkglib_LTLIBRARIES = libbindbackend.la
AM_CPPFLAGS=-I../../pdns $(BOOST_CPPFLAGS) $(POLARSSL_CFLAGS) $(THREADFLAGS)

AM_LFLAGS = -i
AM_YFLAGS = -d --verbose --debug

BUILT_SOURCES=../../pdns/bind-dnssec.schema.sqlite3.sql.h ../../pdns/bindparser.h

EXTRA_DIST=OBJECTFILES OBJECTLIBS

libbindbackend_la_SOURCES=bindbackend2.cc bindbackend2.hh binddnssec.cc ../../pdns/bindparser.yy ../../pdns/bindlexer.l

libbindbackend_la_LDFLAGS=-module -avoid-version

../../pdns/bind-dnssec.schema.sqlite3.sql.h: ../../pdns/bind-dnssec.schema.sqlite3.sql
	( echo 'static char sqlCreate[] __attribute__((unused))=' ; sed 's/$$/"/g' ../../pdns/bind-dnssec.schema.sqlite3.sql | sed 's/^/"/g'  ; echo ';' ) > $@

# for bindparser.h/hh
.hh.h:
	cp $< $@

MAINTAINERCLEANFILES = Makefile.in

phonefsod-usage-service-glue.h: $(SPECS_PATH)/org.shr.phonefso.Usage.xml
	$(DBUSBINDINGTOOL) --mode=glib-server --output=$@ --prefix=phonefsod_usage_service $^

EXTRA_DIST = dbus/phonefsod-usage.xml

bin_PROGRAMS = phonefsod
dbus_sources = phonefsod-usage-service-glue.h


BUILT_SOURCES = $(dbus_sources)

phonefsod_SOURCES = $(dbus_sources) \
	phonefsod.c \
	phonefsod-fso.c \
	phonefsod-fso.h \
	phonefsod-dbus.c \
	phonefsod-dbus.h \
	phonefsod-dbus-common.h \
	phonefsod-dbus-usage.c \
	phonefsod-dbus-usage.h \
	phonefsod-dbus-phoneuid.c \
	phonefsod-dbus-phoneuid.h

phonefsod_CFLAGS = \
	-DDATADIR=\"$(datadir)\" \
	-DPKGDATADIR=\"$(pkgdatadir)\" \
	-DPHONEFSOD_CONFIG=\"$(sysconfdir)/phonefsod.conf\" \
	-DG_LOG_DOMAIN=\"phonefsod\" \
	@DBUS_GLIB_CFLAGS@ \
	@DBUS_CFLAGS@ \
	@FSO_GLIB_CFLAGS@ \
	@FSO_FRAMEWORK_CFLAGS@ \
	-ggdb

phonefsod_LDFLAGS = \
	@DBUS_GLIB_LIBS@ \
	@DBUS_LIBS@ \
	@FSO_GLIB_LIBS@


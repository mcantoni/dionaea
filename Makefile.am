# $Id$

AUTOMAKE_OPTIONS = foreign

SUBDIRS = src include modules

EXTRA_DIST = configure.ac

ENABLED_IHANDLERS=cmdshell.yaml emuprofile.yaml ftp.yaml log_sqlite.yaml store.yaml tftp_download.yaml

install-data-local:
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/run/
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/binaries/
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/bistreams/
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/roots/
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/roots/ftp
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/roots/tftp
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/roots/upnp
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/roots/www
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/dionaea/share/python/http/template/nginx
	$(INSTALL) -t $(DESTDIR)$(localstatedir)/dionaea/share/python/http/template/nginx/ \
	    share/python/http/template/nginx/*.j2
	if [ ! -e $(DESTDIR)$(sysconfdir)/dionaea/ ]; then \
		$(mkinstalldirs) $(DESTDIR)$(sysconfdir); \
		$(mkinstalldirs) $(DESTDIR)$(sysconfdir)/dionaea; \
		$(mkinstalldirs) $(DESTDIR)$(sysconfdir)/dionaea/ihandlers-available/; \
		$(mkinstalldirs) $(DESTDIR)$(sysconfdir)/dionaea/ihandlers-enabled/; \
		$(mkinstalldirs) $(DESTDIR)$(sysconfdir)/dionaea/services-available/; \
		$(mkinstalldirs) $(DESTDIR)$(sysconfdir)/dionaea/services-enabled/; \
		$(INSTALL_DATA) $(srcdir)/conf/dionaea.cfg $(DESTDIR)$(sysconfdir)/dionaea/dionaea.cfg; \
		$(INSTALL_DATA) $(srcdir)/conf/ihandlers/*.yaml $(DESTDIR)$(sysconfdir)/dionaea/ihandlers-available/; \
		$(INSTALL_DATA) $(srcdir)/conf/services/*.yaml $(DESTDIR)$(sysconfdir)/dionaea/services-available/; \
		(cd $(DESTDIR)$(sysconfdir)/dionaea/ihandlers-enabled/ && for filename in ${ENABLED_IHANDLERS}; do ${LN_S} ../ihandlers-available/$${filename}; done); \
		(cd $(DESTDIR)$(sysconfdir)/dionaea/services-enabled/ && find ../services-available/ -type f -exec ${LN_S} {} \;); \
	fi
	$(mkinstalldirs) $(DESTDIR)$(localstatedir)/log
	


# $FreeBSD$

PORTNAME=	iroffer
PORTVERSION=	3.29
PORTREVISION=	1
CATEGORIES=	irc
MASTER_SITES=	http://iroffer.dinoex.net/
PKGNAMESUFFIX=	-dinoex${PKGNAMESUFFIX2}
DISTNAME=	iroffer-dinoex-${PORTVERSION}

MAINTAINER=	dinoex@FreeBSD.org
COMMENT=	An IRC "bot" that makes sharing files via DCC extremely easy

LICENSE=	GPLv2

CONFLICTS=	iroffer-1* iroffer-lamm-1.*

HAS_CONFIGURE=	yes
CONFIGURE_SCRIPT=	Configure
CONFIGURE_ARGS=	CC="${CC}" LDFLAGS="${LDFLAGS}" LOCALBASE="${LOCALBASE}"
ALL_TARGET=	all-lang doc
USE_RC_SUBR=	iroffer-dinoex

IROFFER_DOCS=	README README.modDinoex LIESMICH.modDinoex \
		LICENSE THANKS TODO \
		help-admin-de.txt help-admin-en.txt \
		help-admin-fr.txt help-admin-it.txt \
		doc/iroffer.1.txt doc/iroffer.1.html doc/iroffer.1.ps \
		doc/INSTALL-linux-de.html doc/INSTALL-linux-de.txt \
		doc/INSTALL-linux-en.html doc/INSTALL-linux-en.txt \
		doc/INSTALL-linux-fr.html doc/INSTALL-linux-fr.txt \
		doc/INSTALL-linux-it.html doc/INSTALL-linux-it.txt \
		doc/INSTALL-vhost-de.html doc/INSTALL-vhost-de.txt \
		doc/INSTALL-vhost-en.html doc/INSTALL-vhost-en.txt \
		doc/INSTALL-vhost-fr.html doc/INSTALL-vhost-fr.txt
IROFFER_EXAMPLES= iroffer.cron \
		sample.config beispiel.config exemple.config \
		header.html footer.html ruby-sample.rb
IROFFER_HTDOCS=	iroffer-state.css robots.txt \
		info.txt.rb json.txt.rb md5.txt.rb sfv.txt.rb

OPTIONS_DEFINE=	CURL RUBY UPNP GEOIP
OPTIONS_DEFAULT=CURL RUBY UPNP GEOIP

CURL_LIB_DEPENDS=	libcurl.so:${PORTSDIR}/ftp/curl
CURL_CONFIGURE_ON=	-curl
RUBY_USE=		RUBY=yes LIBRUBY=yes
RUBY_CONFIGURE_ON=	-ruby
UPNP_LIB_DEPENDS=	libminiupnpc.so:${PORTSDIR}/net/miniupnpc
UPNP_CONFIGURE_ON=	-upnp
GEOIP_LIB_DEPENDS=	libGeoIP.so:${PORTSDIR}/net/GeoIP
GEOIP_CONFIGURE_ON=	-geoip

.include <bsd.port.options.mk>

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/iroffer ${STAGEDIR}${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKSRC}/iroffer-de ${STAGEDIR}${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKSRC}/iroffer-it ${STAGEDIR}${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKSRC}/iroffer-fr ${STAGEDIR}${PREFIX}/bin/
	${INSTALL_MAN} ${WRKSRC}/iroffer.1 ${STAGEDIR}${MANPREFIX}/man/man1/
	${INSTALL_MAN} ${WRKSRC}/xdcc.7 ${STAGEDIR}${MANPREFIX}/man/man7/
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}
.for i in ${IROFFER_DOCS}
	${INSTALL_DATA} ${WRKSRC}/${i} ${STAGEDIR}${DOCSDIR}/
.endfor
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	${MKDIR} ${STAGEDIR}${EXAMPLESDIR}/htdocs
.for i in ${IROFFER_HTDOCS}
	${INSTALL_DATA} ${WRKSRC}/htdocs/${i} ${STAGEDIR}${EXAMPLESDIR}/htdocs/
.endfor
.for i in ${IROFFER_EXAMPLES}
	${INSTALL_DATA} ${WRKSRC}/${i} ${STAGEDIR}${EXAMPLESDIR}/
.endfor
.endif

.include <bsd.port.mk>

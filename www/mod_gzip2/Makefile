# Created by: Stefan `Sec` Zehl <sec@42.org>
# $FreeBSD$

PORTNAME=	mod_gzip2
PORTVERSION=	2.1.0
PORTREVISION=	1
CATEGORIES=	www
MASTER_SITES=	http://www.gknw.net/development/apache/httpd-2.0/unix/modules/
DISTNAME=	mod_gzip-${PORTVERSION}

MAINTAINER=	sec@42.org
COMMENT=	Apache 2.x Internet Content Acceleration module

#LICENSE=	AL11

USE_APACHE=	22+
AP_FAST_BUILD=	yes
AP_GENPLIST=	yes
MAKE_ENV+=	"APXS=${APXS}"
USE_GMAKE=	yes

PORTDOCS=	commands.txt samples.txt
PORTEXAMPLES=	mod_gzip2.conf.sample

post-patch:
	@${MV} ${WRKSRC}/mod_gzip.c ${WRKSRC}/${PORTNAME}.c

post-install:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	@${INSTALL_DATA} ${WRKSRC}/my_cfg.txt ${STAGEDIR}${EXAMPLESDIR}/mod_gzip2.conf.sample
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	@${INSTALL_DATA} ${PORTDOCS:S|^|${WRKSRC}/|} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>

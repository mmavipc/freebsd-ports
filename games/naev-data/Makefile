# Created by: Jose Alonso Cardenas Marquez <acm@FreeBSD.org>
# $FreeBSD$

PORTNAME=	data
PORTVERSION=	0.5.3
CATEGORIES=	games
MASTER_SITES=	SF/${PKGNAMEPREFIX:S/-//}/${PKGNAMEPREFIX}${PORTVERSION} \
		${MASTER_SITE_GOOGLE_CODE}
PKGNAMEPREFIX=	naev-
DISTNAME=	${PORTNAME:S/^/n/}-${PORTVERSION}
EXTRACT_SUFX=	#
DIST_SUBDIR=	${PKGNAMEPREFIX:S/-//}

MAINTAINER=	acm@FreeBSD.org
COMMENT=	Naev game data file

PROJECTHOST=	${PKGNAMEPREFIX:S/-//}
NO_BUILD=	yes

DATADIR=	${PREFIX}/share/${PKGNAMEPREFIX:S/-//}
PLIST_FILES=	share/${PKGNAMEPREFIX:S/-//}/${PORTNAME:S/^/n/}-${PORTVERSION}
PLIST_DIRS=	share/${PKGNAMEPREFIX:S/-//}

NO_STAGE=	yes
do-extract:
	@@${MKDIR} ${WRKSRC}
	@${CP} ${_DISTDIR}/${DISTFILES} ${WRKSRC}

do-install:
	@${MKDIR} ${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/${DISTFILES} ${DATADIR}

.include <bsd.port.mk>

# Created by: Cheng-Lung Sung <clsung@FreeBSD.org>
# $FreeBSD$

PORTNAME=	utf8proc
PORTVERSION=	1.1.3
CATEGORIES=	textproc devel
MASTER_SITES=	http://www.flexiguided.de/pub/
DISTNAME=	${PORTNAME}-v${PORTVERSION}

MAINTAINER=	clsung@FreeBSD.org
COMMENT=	UTF-8 processing library

WRKSRC=		${WRKDIR}/${PORTNAME}
ALL_TARGET=	c-library

USE_LDCONFIG=	yes

do-install:
		${INSTALL_PROGRAM} ${WRKSRC}/libutf8proc.so ${STAGEDIR}${PREFIX}/lib/libutf8proc.so.1
		${INSTALL_DATA} ${WRKSRC}/libutf8proc.a ${STAGEDIR}${PREFIX}/lib
		${INSTALL_DATA} ${WRKSRC}/utf8proc.h ${STAGEDIR}${PREFIX}/include
		${LN} -sf libutf8proc.so.0 ${STAGEDIR}${PREFIX}/lib/libutf8proc.so

.include <bsd.port.mk>

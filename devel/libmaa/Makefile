# Created by: chinsan
# $FreeBSD$

PORTNAME=	libmaa
PORTVERSION=	1.3.2
PORTEPOCH=	1
CATEGORIES=	devel
MASTER_SITES=	SF/dict/${PORTNAME}/${PORTNAME}-${PORTVERSION}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Provides a few data structures and helpful functions

# The software was licensed as GPLv2. LGPL20 is for the library.
LICENSE=	LGPL20

OPTIONS_DEFINE=	DOCS

ALL_TARGET=	lib
CPPFLAGS+=	-I${LOCALBASE}/include
GNU_CONFIGURE=	yes
LDFLAGS+=	-L${LOCALBASE}/lib
USE_AUTOTOOLS=	libtool
USE_LDCONFIG=	yes
USES=		gmake

DOCS=		README doc/libmaa.600dpi.ps
PLIST_FILES=	include/maa.h \
		lib/libmaa.a \
		lib/libmaa.la \
		lib/libmaa.so \
		lib/libmaa.so.3
PORTDOCS=	${DOCS:T}

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}/
	cd ${WRKSRC}/ && ${INSTALL_DATA} ${DOCS} ${STAGEDIR}${DOCSDIR}/
.endif

.include <bsd.port.mk>

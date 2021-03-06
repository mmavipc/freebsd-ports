# Created by: Adam Weinberger <adamw@FreeBSD.org>
# $FreeBSD$

PORTNAME=	mdh
PORTVERSION=	1.9.60
PORTREVISION=	6
CATEGORIES=	deskutils gnome
MASTER_SITES=	http://www.gozer.org/programs/gtk/files/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	GTK2-based toolbar, like a smaller GNOME panel

USE_BZIP2=	yes
USE_GNOME=	gtk20
USES=		gmake pkgconfig
GNU_CONFIGURE=	yes

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

.if defined(WITHOUT_GTOP)
CONFIGURE_ARGS+=	--disable-gtop
.else
LIB_DEPENDS+=	libgtop-2.0.so:${PORTSDIR}/devel/libgtop
.endif

.if defined(WITHOUT_CURL)
CONFIGURE_ARGS+=	--disable-curl
.else
LIB_DEPENDS+=	libcurl.so:${PORTSDIR}/ftp/curl
.endif

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e 's| make| $$(MAKE)|g' ${WRKSRC}/Makefile
	@${REINPLACE_CMD} -e 's|\.\./lib/getopt/getopt\.c||g ; \
		 s|\.\./lib/getopt/getopt1\.c||g ; \
		 s|-I../lib/getopt||g ; \
		 s|$$(CC) -g|$$(CC)|g ; \
		 s|@INSTALL@ -m 0775|@INSTALL_PROGRAM@|g ; \
		 s|cp -p|@INSTALL_DATA@|g' ${WRKSRC}/src/Makefile.in
	@${REINPLACE_CMD} -e 's|"getopt\.h"|<getopt.h>|g' ${WRKSRC}/src/mdh.c
	@${REINPLACE_CMD} -e '/<curl\/types.h>/d' ${WRKSRC}/src/curl.c

post-install:
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${DOCSDIR}
.endif

.include <bsd.port.mk>

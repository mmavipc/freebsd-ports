# Created by: Pedro Giffuni
# $FreeBSD$

PORTNAME=	amberfish
PORTVERSION=	1.6.4
CATEGORIES=	textproc databases
MASTER_SITES=	SF/${PORTNAME}/Amberfish%20source%20-%20stable/${PORTVERSION}	\
		http://etymon.com/software/amberfish/stable/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	General purpose text retrieval Software

LIB_DEPENDS=	libxerces-c.so.27:${PORTSDIR}/textproc/xerces-c2

USES=		gmake
GNU_CONFIGURE=	yes
ALL_TARGET=	all html

PLIST_FILES=	bin/af man/man1/af.1.gz
PORTDOCS=	*

OPTIONS_DEFINE=	DOCS

post-extract:
	${INSTALL_DATA} ${FILESDIR}/porter.cc ${WRKSRC}/src

post-patch:
	@${REINPLACE_CMD} -e \
		's|$${MAKEFLAGS} ||' ${WRKSRC}/Makefile
	@${REINPLACE_CMD} -e \
		's|cp |$${BSD_INSTALL_MAN} |' ${WRKSRC}/doc/Makefile.in
	@${REINPLACE_CMD} -e \
		's|-O3 |@CFLAGS@ | ; \
		s|make strip|| ; \
		s|cp |$${BSD_INSTALL_PROGRAM} |' ${WRKSRC}/src/Makefile.in

post-install:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/amberfish.png ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/doc/html/*.html ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>

# Created by: Michael L. Hostbaek (mich@freebsdcluster.org)
# $FreeBSD$

PORTNAME=	nInvaders
PORTVERSION=	0.1.1
CATEGORIES=	games
MASTER_SITES=	SF
DISTNAME=	ninvaders-${PORTVERSION}

MAINTAINER=	mich@FreeBSD.org
COMMENT=	The nIvaders game is a Space Invaders clone for ncurses


NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e "s|^CC|#CC|g" \
	-e "s|^CFLAGS|#CFLAGS|g" ${WRKSRC}/Makefile

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME} ${PREFIX}/bin

.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${DOCSDIR}
.endif

.include <bsd.port.mk>

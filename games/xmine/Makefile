# Created by: joerg
# $FreeBSD$

PORTNAME=	xmine
PORTVERSION=	1.0.3
PORTREVISION=	2
CATEGORIES=	games
MASTER_SITES=	ftp://ftp.sw.ru/pub/x11/ \
		${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	joerg
DISTNAME=	${PORTNAME}-${PORTVERSION}-Xaw

MAINTAINER=	joerg@FreeBSD.org
COMMENT=	The `Athena' port of the xminesweeper game

LIB_DEPENDS=	Xaw3d:${PORTSDIR}/x11-toolkits/Xaw3d

USES=		imake
USE_XORG=	x11 xaw xext xmu xt xpm sm ice
MAN6=		xmine.6
MANCOMPRESSED=	no

NO_STAGE=	yes
.include <bsd.port.mk>

# Created by: janek@gaja.ipan.lublin.pl
# $FreeBSD$

PORTNAME=	xmix
PORTVERSION=	2.1
PORTREVISION=	2
CATEGORIES=	audio
MASTER_SITES=	${MASTER_SITE_SUNSITE}
MASTER_SITE_SUBDIR=	apps/sound/mixers

PATCH_SITES=	${MASTER_SITES}
PATCH_SITE_SUBDIR=	${MASTER_SITE_SUBDIR}
PATCHFILES=	xmix-2.1.mixers.patch

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Mixer for X Window System

USES=		imake
WRKSRC=		${WRKDIR}/xmix
USE_XORG=	x11 xext xmu xaw xt sm ice

PLIST_FILES=	bin/xmix lib/X11/app-defaults/XMix \
		man/man1/xmix.1.gz

pre-build:
	${CP} ${WRKSRC}/xmix.1 ${WRKSRC}/xmix.man

post-install:
	${INSTALL_DATA} ${WRKSRC}/XMix ${STAGEDIR}${PREFIX}/lib/X11/app-defaults

.include <bsd.port.mk>

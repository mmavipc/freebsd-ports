# Created by: Jan Stocker <Jan.Stocker@t-online.de>
# $FreeBSD$

PORTNAME=	tuxpuck
PORTVERSION=	0.8.2
PORTREVISION=	18
CATEGORIES=	games
MASTER_SITES=	http://www.sourcefiles.org/Games/Sports/Miscellaneous/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Shufflepuck Cafe Clone

LICENSE=	GPLv2

LIB_DEPENDS=	libjpeg.so:${PORTSDIR}/graphics/jpeg \
		libpng15.so:${PORTSDIR}/graphics/png \
		libvorbis.so:${PORTSDIR}/audio/libvorbis \
		libfreetype.so:${PORTSDIR}/print/freetype2

USE_SDL=	sdl
USES=		gmake
ALL_TARGET=	${PORTNAME}
MAKE_JOBS_UNSAFE=	yes

PLIST_FILES=	bin/${PORTNAME} man/man6/tuxpuck.6.gz

post-patch:
.for i in intro.c timer.c tuxpuck.c tuxpuck.h video.c
	@${REINPLACE_CMD} -e \
		's|timer_create|_timer_create|g' ${WRKSRC}/${i}
.endfor
.for i in data utils
	@${REINPLACE_CMD} -e \
		's|^CC|#CC| ; \
		 s|^CFLAGS|#CFLAGS| ; \
		 s|sdl-config|$$(SDL_CONFIG)|' ${WRKSRC}/${i}/Makefile
.endfor

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/man/tuxpuck.6.gz ${STAGEDIR}${MAN6PREFIX}/man/man6

.include <bsd.port.mk>

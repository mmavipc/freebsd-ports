# Created by: Veniamin Gvozdikov <vg@FreeBSD.org>
# $FreeBSD$

PORTNAME=	lastfm
PORTVERSION=	2.1.30
PORTREVISION=	2
CATEGORIES=	audio
MASTER_SITES=	http://cdn.last.fm/client/Linux/
PKGNAMESUFFIX=	-desktop
DISTNAME=	Last.fm-${PORTVERSION}

MAINTAINER=	vg@FreeBSD.org
COMMENT=	Official Last.fm desktop application suite

LICENSE=	GPLv3

LIB_DEPENDS=	liblastfm.so:${PORTSDIR}/audio/liblastfm \
		libavcodec.so:${PORTSDIR}/multimedia/ffmpeg \
		libgpod.so:${PORTSDIR}/audio/libgpod

USES=		pkgconfig qmake
USE_BZIP2=	yes
USE_QT4=	gui linguist_build moc_build network phonon \
		rcc_build uic_build webkit xml
LASTFM=		${PORTNAME}${PKGNAMESUFFIX}
SUB_FILES=	${LASTFM}.sh

WRKSRC=		${WRKDIR}/${PORTNAME}${PKGNAMESUFFIX}-${PORTVERSION}

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}
	${INSTALL_SCRIPT} ${WRKDIR}/${LASTFM}.sh ${STAGEDIR}${PREFIX}/bin/${LASTFM}
	${INSTALL_PROGRAM} ${WRKSRC}/_bin/Last.fm\ Scrobbler ${STAGEDIR}${DATADIR}
	${INSTALL_LIB} ${WRKSRC}/_bin/lib*.so* ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/app/client/Last.fm\ Scrobbler.css \
		${STAGEDIR}${DATADIR}

.include <bsd.port.mk>

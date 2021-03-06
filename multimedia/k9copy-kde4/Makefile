# Created by: Alexander V. Ribchansky <triosoft@triosoft.com.ua>
# $FreeBSD$

PORTNAME=	k9copy
PORTVERSION=	2.3.4
PORTREVISION=	10
CATEGORIES=	multimedia kde
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}-kde4/${PORTVERSION}
DISTNAME=	${PORTNAME}-${PORTVERSION}-Source

MAINTAINER=	egoliveira@gmail.com
COMMENT=	DVD-9 to DVD-5 shrinking application for KDE

LICENSE=	GPLv2

LIB_DEPENDS=	libxine.so:${PORTSDIR}/multimedia/libxine \
		libmpeg2.so:${PORTSDIR}/multimedia/libmpeg2 \
		libavcodec0.so:${PORTSDIR}/multimedia/ffmpeg0

USES=		cmake gettext
USE_KDE4=	kdeprefix kdelibs automoc4
USE_QT4=	moc_build qmake_build rcc_build uic_build

CFLAGS=		-I${LOCALBASE}/include/ffmpeg0
CPPFLAGS=	-I${LOCALBASE}/include/ffmpeg0
CXXFLAGS=	-I${LOCALBASE}/include/ffmpeg0

OPTIONS_DEFINE=	MENCODER MPLAYER DVDAUTHOR
MENCODER_DESC=	MEncoder support
MPLAYER_DESC=	MPlayer support
DVDAUTHOR_DESC=	DVD Author support

MENCODER_RUN_DEPENDS=	mencoder:${PORTSDIR}/multimedia/mencoder
MPLAYER_RUN_DEPENDS=	mplayer:${PORTSDIR}/multimedia/mplayer
DVDAUTHOR_RUN_DEPENDS=	dvdauthor:${PORTSDIR}/multimedia/dvdauthor

post-patch:
	@${REINPLACE_CMD} -e 's,%%LOCALBASE%%,${LOCALBASE},g' ${WRKSRC}/cmake/*.cmake
	@${REINPLACE_CMD} \
		-e 's,swscale,swscale0,' \
		-e 's,avcodec,avcodec0,' \
		-e 's,avformat,avformat0,' \
		${WRKSRC}/CMakeLists.txt

.include <bsd.port.mk>

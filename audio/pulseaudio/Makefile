# Created by: Joe Marcus Clarke <marcus@FreeBSD.org>
# $FreeBSD$
#   $MCom: ports-stable/audio/pulseaudio/Makefile,v 1.7 2010/06/25 20:35:01 kwm Exp $

# !!!NOTE!!! Any PORTVERSION update to this port must be accompanied by
# PORTREVISION bumps to audio/gnome-media, sysutils/gnome-settings-daemon,
# and audio/gstreamer-plugins-pulse.
#

PORTNAME=	pulseaudio
PORTVERSION=	0.9.23
PORTREVISION=	2
CATEGORIES=	audio
MASTER_SITES=	http://freedesktop.org/software/pulseaudio/releases/

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Sound server for UNIX

LIB_DEPENDS=	libsamplerate.so:${PORTSDIR}/audio/libsamplerate \
		libsndfile.so:${PORTSDIR}/audio/libsndfile \
		libspeexdsp.so:${PORTSDIR}/audio/speex \
		libdbus-1.so:${PORTSDIR}/devel/dbus \
		libgdbm.so:${PORTSDIR}/databases/gdbm \
		libexecinfo.so:${PORTSDIR}/devel/libexecinfo \
		libck-connector.so:${PORTSDIR}/sysutils/consolekit

USE_GNOME=	gnomehack glib20 intltool ltverhack
NO_STAGE=	yes
USE_XORG=	x11 sm xtst ice
USE_LDCONFIG=	yes
USES=		gettext gmake pkgconfig
GNU_CONFIGURE=	yes
USE_AUTOTOOLS=	libltdl libtool
MAKE_JOBS_UNSAFE=yes
CONFIGURE_ENV=	PTHREAD_CFLAGS="${PTHREAD_CFLAGS}" \
		PTHREAD_LIBS="${PTHREAD_LIBS}" \
		OPENSSL_CFLAGS="-I/usr/include" \
		OPENSSL_LIBS="-lcrypto -lssl" \
		LIBS="-lm -lintl" \
		ac_cv_header_linux_input_h=
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

.if ${CC} == clang
CFLAGS+=	-fheinous-gnu-extensions
.endif

CONFIGURE_ARGS=	--localstatedir=/var \
		--with-database=gdbm \
		--without-caps \
		--disable-alsa \
		--disable-udev \
		--disable-gtk2 \
		--disable-lirc # untested

USERS=		pulse
GROUPS=		pulse pulse-access pulse-rt

OPTIONS_DEFINE=	JACK AVAHI HAL GCONF
OPTIONS_DEFAULT=	AVAHI HAL GCONF

PULSE_VERSION=	${PORTVERSION}
PLIST_SUB=	PULSE_VERSION=${PULSE_VERSION}

MAN1=		esdcompat.1 pabrowse.1 pacat.1 pacmd.1 pactl.1 padsp.1 \
		paplay.1 pasuspender.1 pax11publish.1 pulseaudio.1
MAN5=		default.pa.5 pulse-client.conf.5 pulse-daemon.conf.5

.include <bsd.port.pre.mk>

.if ${PORT_OPTIONS:MJACK}
LIB_DEPENDS+=	libjack.so:${PORTSDIR}/audio/jack
PLIST_SUB+=	JACK=""
.else
PLIST_SUB+=	JACK="@comment "
CONFIGURE_ARGS+=--disable-jack
.endif

.if ${PORT_OPTIONS:MAVAHI}
LIB_DEPENDS+=	libavahi-client.so:${PORTSDIR}/net/avahi-app
PLIST_SUB+=	AVAHI=""
.else
CONFIGURE_ARGS+=--disable-avahi
PLIST_SUB+=	AVAHI="@comment "
.endif

.if ${PORT_OPTIONS:MHAL}
LIB_DEPENDS+=	libhal.so:${PORTSDIR}/sysutils/hal
PLIST_SUB+=	HAL=""
.else
CONFIGURE_ARGS+=--disable-hal
PLIST_SUB+=	HAL="@comment "
.endif

.if ${PORT_OPTIONS:MGCONF}
USE_GNOME+=	gconf2
PLIST_SUB+=	GCONF=""
.else
CONFIGURE_ARGS+=--disable-gconf
PLIST_SUB+=	GCONF="@comment "
.endif

.if ((${OSVERSION} >= 800000) && (${OSVERSION} < 802504)) || \
	((${OSVERSION} >= 900000) && (${OSVERSION} < 900037))
EXTRA_PATCHES+=	${FILESDIR}/extra-src_modules_oss_module-oss.c
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|%%LOCALBASE%%|${LOCALBASE}|g' \
		${WRKSRC}/src/daemon/default.pa.in
	@${REINPLACE_CMD} -e 's|-Wmissing-include-dirs||g' \
		${WRKSRC}/configure

post-install:
	${MKDIR} ${PREFIX}/etc/pulse
.for ii in default.pa daemon.conf client.conf system.pa
	${INSTALL_DATA} ${WRKSRC}/src/${ii} \
		${PREFIX}/etc/pulse/${ii}-dist
. if !exists(${PREFIX}/etc/pulse/${II})
	${INSTALL_DATA} ${WRKSRC}/src/${ii} \
		${PREFIX}/etc/pulse/${ii}
. endif
.endfor

.include <bsd.port.post.mk>

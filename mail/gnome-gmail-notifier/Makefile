# $FreeBSD$

PORTNAME=	gnome-gmail-notifier
PORTVERSION=	0.10.1
PORTREVISION=	4
CATEGORIES=	mail deskutils
MASTER_SITES=	GOOGLE_CODE

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Gmail Inbox Monitor for the GNOME2 desktop

LIB_DEPENDS=	libnotify.so:${PORTSDIR}/devel/libnotify \
		libsoup-2.4.so:${PORTSDIR}/devel/libsoup \
		libgnome-keyring.so:${PORTSDIR}/security/libgnome-keyring

GNU_CONFIGURE=	yes
USE_BZIP2=	yes
USES=		gettext gmake pkgconfig
USE_GNOME=	glib20 gtk20 gconf2 libxml2 librsvg2
USE_GSTREAMER=	good
LDFLAGS+=	-L${LOCALBASE}/lib -lintl

post-patch:
	@${REINPLACE_CMD} -e 's|@DATADIRNAME@|share|' ${WRKSRC}/po/Makefile.in.in
	@${REINPLACE_CMD} -e 's|<glib/gthread.h>|<glib.h>|g' ${WRKSRC}/src/main.h

.include <bsd.port.mk>

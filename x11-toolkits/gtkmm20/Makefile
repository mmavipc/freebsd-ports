# Created by: Martin Klaffenboeck <martin.klaffenboeck@gmx.at>
# $FreeBSD$
#    $MCom: ports/x11-toolkits/gtkmm20/Makefile,v 1.11 2006/09/10 00:51:17 mezz Exp $

PORTNAME=	gtkmm
PORTVERSION=	2.2.12
PORTREVISION?=	13
CATEGORIES=	x11-toolkits
MASTER_SITES=	GNOME/sources/${PORTNAME}/2.2
PKGNAMESUFFIX=	20
DIST_SUBDIR=	gnome2

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	C++ wrapper for Gtk+, Pango, Atk, and Glib

USE_BZIP2=	yes

.if !defined(REFERENCE_PORT)

LIB_DEPENDS=	sigc-1.2.5:${PORTSDIR}/devel/libsigc++12
BUILD_DEPENDS=	gm4:${PORTSDIR}/devel/m4

USE_AUTOTOOLS=	libtool
USES=		pathfix gmake pkgconfig
GNU_CONFIGURE=	yes
USE_LDCONFIG=	yes
USE_GNOME=	lthack gtk20
CONFIGURE_ARGS=	--enable-static=yes \
		--with-sigc-prefix=${LOCALBASE}

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e 's|glib/gmessages.h|glib/gtestutils.h|g' \
		${WRKSRC}/glib/src/*.ccg ${WRKSRC}/glib/glibmm/*.* \
		${WRKSRC}/gtk/src/*.* ${WRKSRC}/gtk/gtkmm/*.* \
		${WRKSRC}/demos/gtk-demo/*.cc
	@${REINPLACE_CMD} -e 's|glib/.*\.h>|glib.h>|g' \
		${WRKSRC}/glib/glibmm/*.cc ${WRKSRC}/glib/glibmm/*.h \
		${WRKSRC}/gtk/gtkmm/textbuffer.cc
.for d in docs examples tests
	@${REINPLACE_CMD} -e '/^SUBDIRS =/s/${d}//' ${WRKSRC}/Makefile.in
.endfor

.include <bsd.port.mk>

.endif

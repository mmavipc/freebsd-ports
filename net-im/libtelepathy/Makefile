# $FreeBSD$
#    $MCom: ports/net-im/libtelepathy/Makefile,v 1.3 2008/02/27 14:00:06 ahze Exp $

PORTNAME=	libtelepathy
PORTVERSION=	0.3.3
PORTREVISION=	1
CATEGORIES=	net-im devel
MASTER_SITES=	http://telepathy.freedesktop.org/releases/${PORTNAME}/

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Flexible Communications Framework

LIB_PC_DEPENDS=	dbus-glib-1.pc:${PORTSDIR}/devel/dbus-glib

BUILD_DEPENDS=	xsltproc:${PORTSDIR}/textproc/libxslt
LIB_DEPENDS=	telepathy-glib.0:${PORTSDIR}/net-im/telepathy-glib

BUILD_DEPENDS+=	${LIB_PC_DEPENDS:C|^|${LOCALBASE}/libdata/pkgconfig/|g}
RUN_DEPENDS+=	${LIB_PC_DEPENDS:C|^|${LOCALBASE}/libdata/pkgconfig/|g}

USE_PYTHON_BUILD=	yes
USES=		gmake pkgconfig
USE_LDCONFIG=	yes
USE_GNOME=	gnomehack glib20 ltverhack
USE_AUTOTOOLS=	libtool

NO_STAGE=	yes
.include <bsd.port.mk>

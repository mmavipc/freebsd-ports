# Created by: Joe Marcus Clarke <marcus@FreeBSD.org>
# $FreeBSD$
#   $MCom: ports/sysutils/gconf-editor/Makefile,v 1.85 2010/09/27 18:22:59 kwm Exp $

PORTNAME=	gconf-editor
PORTVERSION=	2.32.0
PORTREVISION=	1
PORTEPOCH=	1
CATEGORIES=	sysutils gnome
MASTER_SITES=	GNOME
DIST_SUBDIR=	gnome2

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	A gconf database editor for the GNOME 2 environment

USE_BZIP2=	yes
USES=		gettext gmake pkgconfig
INSTALLS_OMF=	yes
INSTALLS_ICONS=	yes
USE_GNOME=	gnomeprefix intlhack gnomehack libgnomeui gnomedocutils
GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

MAN1=		gconf-editor.1
GCONF_SCHEMAS=	gconf-editor.schemas

NO_STAGE=	yes
.include <bsd.port.mk>

# Created by: Martin Wilke (miwi@FreeBSD.org)
# $FreeBSD$

PORTNAME=	xfce4-datetime-plugin
PORTVERSION=	0.6.2
PORTREVISION=	1
CATEGORIES=	x11-clocks xfce
MASTER_SITES=	${MASTER_SITE_XFCE}
MASTER_SITE_SUBDIR=src/panel-plugins/${PORTNAME}/${PORTVERSION:R}
DIST_SUBDIR=	xfce4

MAINTAINER=	xfce@FreeBSD.org
COMMENT=	Datetime panel plugin for the Xfce desktop

LICENSE=	GPLv2

USE_BZIP2=	yes
INSTALLS_ICONS=	yes
GNU_CONFIGURE=	yes
USE_GNOME=	gtk20 intltool intlhack
USE_XFCE=	configenv libmenu libutil panel
USES=		pkgconfig gettext gmake

.include <bsd.port.mk>

# Created by: Alexander Nedotsukov <bland@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gnomephotoprinter
PORTVERSION=	0.7.0
PORTREVISION=	9
CATEGORIES=	print gnome
MASTER_SITES=	http://www.fogman.de/gpp/
DISTNAME=	gpp-${PORTVERSION}
DIST_SUBDIR=	gnome2

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Gnome Photo Printer is intended for printing photos in an easy way

USE_GNOME=	gnomehack gnomeprefix libgnomeui libglade2 libgnomeprintui \
		gnomevfs2
USES=		gettext gmake pkgconfig
GNU_CONFIGURE=	yes
INSTALLS_ICONS=	yes

NO_STAGE=	yes
.include <bsd.port.mk>

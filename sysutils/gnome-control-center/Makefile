# Created by: Joe Marcus Clarke <marcus@FreeBSD.org>
# $FreeBSD$
#   $MCom: ports/sysutils/gnome-control-center/Makefile,v 1.214 2010/11/18 11:46:09 kwm Exp $

PORTNAME=	gnome-control-center
PORTVERSION=	2.32.1
PORTREVISION=	1
CATEGORIES=	sysutils gnome
MASTER_SITES=	GNOME
DIST_SUBDIR=	gnome2

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Control center for GNOME 2 project

LIB_DEPENDS=	canberra-gtk.0:${PORTSDIR}/audio/libcanberra \
		dbus-glib-1.2:${PORTSDIR}/devel/dbus-glib \
		polkit-gobject-1.0:${PORTSDIR}/sysutils/polkit \
		unique-1.0.2:${PORTSDIR}/x11-toolkits/unique
BUILD_DEPENDS=	${LOCALBASE}/libexec/gnome-settings-daemon:${PORTSDIR}/sysutils/gnome-settings-daemon
RUN_DEPENDS=	gnome-eject:${PORTSDIR}/sysutils/gnome-mount \
		${LOCALBASE}/libexec/gnome-settings-daemon:${PORTSDIR}/sysutils/gnome-settings-daemon

USE_BZIP2=	yes
USES=		gettext gmake pkgconfig
GNOME_DESKTOP_VERSION=2
USE_GSTREAMER=	good
WANT_GNOME=	yes
USE_GNOME=	gnomeprefix gnomehack intlhack metacity gnomemenus \
		desktopfileutils libgnomekbd gnomedesktop librsvg2 gconf2
USE_XORG=	xscrnsaver
GNU_CONFIGURE=	yes
INSTALLS_OMF=	yes
INSTALLS_ICONS=	yes
USE_LDCONFIG=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

GCONF_SCHEMAS=	control-center.schemas fontilus.schemas \
		gnome-control-center.schemas

.if defined(PACKAGE_BUILDING)
.undef WITHOUT_GNOME
WITH_GNOME=	yes
.endif

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${HAVE_GNOME:Mevolutiondataserver}!=""
USE_GNOME+=	evolutiondataserver
CONFIGURE_ARGS+=--enable-aboutme
PLIST_SUB+=	ABOUTME=""
.else
CONFIGURE_ARGS+=--disable-aboutme
PLIST_SUB+=	ABOUTME="@comment "
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|%%LOCALBASE%%|${LOCALBASE}|' \
	    	${WRKSRC}/capplets/common/gnome-theme-info.c
	@${REINPLACE_CMD} -e 's|/usr/sbin|${PREFIX}/sbin|g' \
		${WRKSRC}/capplets/display/org.gnome.randr.policy.in
	@${REINPLACE_CMD} -e 's|"libslab"|"libnoslab"|g' \
		${WRKSRC}/configure

post-install:
	@-update-desktop-database

.include <bsd.port.post.mk>

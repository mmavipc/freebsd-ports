# Created by: Nikola Lecic <nikola.lecic@anthesphoria.net>
# $FreeBSD$

PORTNAME=	m17n-im-config
PORTVERSION=	0.9.0
PORTREVISION=	7
CATEGORIES=	textproc
MASTER_SITES=	http://www.m17n.org/common/im-config/ \
		http://anthesphoria.net/FreeBSD/ports/distfiles/

MAINTAINER=	nikola.lecic@anthesphoria.net
COMMENT=	A GUI for per-user configuration of m17n-lib input methods

LIB_DEPENDS=	m17n.4:${PORTSDIR}/devel/m17n-lib

MAKE_JOBS_UNSAFE=	yes

USE_AUTOTOOLS=	libtool
USE_GNOME=	gtk20 intltool intlhack glib20
USES=		gettext pkgconfig
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes

DESKTOP_ENTRIES="M17N-IM Configuration" \
		"${COMMENT}" \
		"" \
		"m17n-im-config" \
		"Settings;" \
		true

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MNLS}
USES+=		gettext
PLIST_SUB+=	NLS=""
.else
CONFIGURE_ARGS+=	--disable-nls
PLIST_SUB+=	NLS="@comment "
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|^pkgconfigdir = $${libdir}/pkgconfig|pkgconfigdir = $${prefix}/libdata/pkgconfig|' \
		${WRKSRC}/Makefile.in

.include <bsd.port.mk>

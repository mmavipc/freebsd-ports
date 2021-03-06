# Created by: Craig Leres <leres@ee.lbl.gov>
# $FreeBSD$

PORTNAME=	hostapd
PORTVERSION=	2.0
CATEGORIES=	net
MASTER_SITES=	http://hostap.epitest.fi/releases/

MAINTAINER=	leres@ee.lbl.gov
COMMENT=	IEEE 802.11 AP, IEEE 802.1X/WPA/WPA2/EAP/RADIUS Authenticator

LICENSE=	GPLv2 BSD
LICENSE_COMB=	dual

USE_GMAKE=	yes
BUILD_WRKSRC=	${WRKSRC}/${PORTNAME}

MAN1=		hostapd_cli.1
MAN8=		hostapd.8

PLIST_FILES=	sbin/hostapd \
		sbin/hostapd_cli

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${ARCH} == "ia64" || ${ARCH} == "powerpc" || ${ARCH} == "sparc64"
BROKEN=		Does not compile on ia64, powerpc, or sparc64
.endif

post-patch-script:
	@${REINPLACE_CMD} -e 's|@$$(E) "  CC " $$<|@$$(E) "  $$(CC) " $$<|' \
		${BUILD_WRKSRC}/Makefile

do-configure:
	${CP} ${FILESDIR}/config ${WRKSRC}/hostapd/.config

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/hostapd/hostapd ${PREFIX}/sbin
	${INSTALL_PROGRAM} ${WRKSRC}/hostapd/hostapd_cli ${PREFIX}/sbin
	${INSTALL_MAN} ${WRKSRC}/hostapd/${MAN1} ${MAN1PREFIX}/man/man1
	${INSTALL_MAN} ${WRKSRC}/hostapd/${MAN8} ${MAN8PREFIX}/man/man8

.include <bsd.port.post.mk>

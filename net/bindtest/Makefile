# Created by: Janos Mohacsi <janos.mohacsi@bsd.hu>
# $FreeBSD$

PORTNAME=	bindtest
PORTVERSION=	1.56
PORTREVISION=	1
CATEGORIES=	net ipv6
MASTER_SITES=	ftp://ftp.kame.net/pub/kame/misc/ \
		ftp://sunsite.cnlab-switch.ch/mirror/kame/misc/ \
		ftp://ftp.pasta.cs.uit.no/pub/IPv6/kame/misc/ \
		ftp://ftp.ipv6.uni-leipzig.de/pub/ftp.kame.net/pub/kame/misc/
DISTNAME=	${PORTNAME}
EXTRACT_SUFX=	.tgz
IGNOREFILES=	${DISTNAME}${EXTRACT_SUFX}

MAINTAINER=	jmohacsi@bsd.hu
COMMENT=	Test bind() semantics of IPv6 sockets

MAN1=		bindtest.1

NO_STAGE=	yes
do-install:
		${INSTALL_PROGRAM} ${WRKSRC}/bindtest ${PREFIX}/bin/
		${INSTALL_SCRIPT} ${WRKSRC}/test.sh ${PREFIX}/bin/bindtest.sh
		${INSTALL_MAN} ${WRKSRC}/${MAN1} ${MAN1PREFIX}/man/man1

.include <bsd.port.mk>

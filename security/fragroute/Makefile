# Created by: Dominic Marks <dominic.marks@btinternet.com>
# $FreeBSD$

PORTNAME=	fragroute
PORTVERSION=	1.2
PORTREVISION=	11
CATEGORIES=	security net
MASTER_SITES=	http://monkey.org/~dugsong/fragroute/ \
		${MASTER_SITE_PACKETSTORM}
MASTER_SITE_SUBDIR=	UNIX/security

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Tool for intercepting, modifying, and rewriting egress traffic

LIB_DEPENDS=	dnet.1:${PORTSDIR}/net/libdnet \
		event-1.4:${PORTSDIR}/devel/libevent

LICENSE=	BSD
GNU_CONFIGURE=	yes
CONFIGURE_ARGS+=	--with-libdnet=${LOCALBASE} \
			--with-libevent=${LOCALBASE} --with-pcap

MAN8=	fragroute.8 fragtest.8

SCRIPTS=	README.snort base-1 frag-1 frag-2 frag-3 frag-4 frag-5 \
	frag-6 frag-7-unix frag-7-win32 ins-2 ins-3 tcbc-2 tcp-3 tcp-5 \
	tcp-7 tcp-9

NO_STAGE=	yes
pre-install:
	${MKDIR} ${DATADIR}
.for FILE in ${SCRIPTS}
	${INSTALL_DATA} ${WRKSRC}/scripts/${FILE} ${DATADIR}
.endfor

.include <bsd.port.mk>

# Created by: Norikatsu Shigemura <nork@FreeBSD.org>
# $FreeBSD$

PORTNAME=	flare
PORTVERSION=	1.0.9
PORTREVISION=	4
CATEGORIES=	databases
MASTER_SITES=	http://labs.gree.jp/data/source/
PKGNAMESUFFIX=	-db
EXTRACT_SUFX=	.tgz

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Flare - distributed and persistent key-value storage

LIB_DEPENDS=	libboost_program_options.so:${PORTSDIR}/devel/boost-libs \
		libtokyocabinet.so:${PORTSDIR}/databases/tokyocabinet

LICENSE=	GPLv2

GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include -DHAVE_KQUEUE
LDFLAGS+=	-L${LOCALBASE}/lib

USE_RC_SUBR=	flared flarei
SUB_FILES=	pkg-message

NO_STAGE=	yes
post-install:
	@${INSTALL} -d ${_BINOWNGRP} -m 0750 /var/db/flare
	@${INSTALL_DATA} ${WRKSRC}/etc/flared.conf ${PREFIX}/etc/flared.conf-dist
	@[ -f ${PREFIX}/etc/flared.conf ] || \
		${CP} -p ${PREFIX}/etc/flared.conf-dist ${PREFIX}/etc/flared.conf
	@${INSTALL_DATA} ${WRKSRC}/etc/flarei.conf ${PREFIX}/etc/flarei.conf-dist
	@[ -f ${PREFIX}/etc/flarei.conf ] || \
		${CP} -p ${PREFIX}/etc/flarei.conf-dist ${PREFIX}/etc/flarei.conf
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.pre.mk>

.if ${ARCH} == "sparc64"
BROKEN=		Does not compile on sparc64
.endif

# NOT TESTED YET
#CONFIGURE_ARGS+=--enable-mysql-replication
#CONFIGURE_ARGS+=--enable-flarefs --with-fuse=${LOCALBASE}
#CONFIGURE_ARGS+=--enable-memory-allocation-check

.include <bsd.port.post.mk>

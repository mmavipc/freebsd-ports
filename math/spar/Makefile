# Created by: ijliao
# $FreeBSD$

PORTNAME=	spar
PORTVERSION=	0.5.10
PORTREVISION=	1
CATEGORIES=	math devel
MASTER_SITES=	SF/${PORTNAME}/Spar/${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	A modular math parser

USE_AUTOTOOLS=	libtool
GNU_CONFIGURE=	yes
USE_CSTD=	gnu89
USE_LDCONFIG=	yes

MAN1=	spar.1

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e 's|$${CONFIG_SHELL-/bin/sh} $$ac_aux_dir|$$ac_aux_dir|' \
		${WRKSRC}/configure
	@${REINPLACE_CMD} -e "s,-ldl,,g" \
		${WRKSRC}/lib/Makefile.in ${WRKSRC}/lib/module/Makefile.in

.include <bsd.port.mk>

# Created by: Matthew Dillon <dillon@backplane.com>
# $FreeBSD$

PORTNAME=	jikes
PORTVERSION=	1.22
PORTREVISION=	1
CATEGORIES=	java
MASTER_SITES=	SF/${PORTNAME}/Jikes/${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Java source to byte-code compiler made available by IBM

MAN1=		jikes.1

PLIST_SUB=	PORTVERSION=${PORTVERSION}
GNU_CONFIGURE=	yes
USE_GMAKE=	yes
USES=		iconv
USE_BZIP2=	yes

CONFIGURE_ARGS=	CPPFLAGS="-I${LOCALBASE}/include" LIBS="-L${LOCALBASE}/lib"

NO_STAGE=	yes
.include <bsd.port.mk>

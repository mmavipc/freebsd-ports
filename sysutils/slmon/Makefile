# Created by: ijliao
# $FreeBSD$

PORTNAME=	slmon
PORTVERSION=	0.5.13
PORTREVISION=	7
CATEGORIES=	sysutils
MASTER_SITES=	SF/${PORTNAME}/SLmon/${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	S-Lang System Monitor

LIB_DEPENDS=	gtop-2.0.7:${PORTSDIR}/devel/libgtop \
		slang.2:${PORTSDIR}/devel/libslang2

BROKEN=		Does not build
DEPRECATED=	Broken for more than 6 month
EXPIRATION_DATE=	2014-02-27

USE_GMAKE=	yes
GNU_CONFIGURE=	yes

MAN1=		slmon.1
PLIST_FILES=	bin/slmon

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib -lncurses -lm

NO_STAGE=	yes
.include <bsd.port.pre.mk>

# For gmake>=3.82
post-patch:
	@${REINPLACE_CMD} -e 's/^   */	/' ${WRKSRC}/Makefile.in

.if ${OSVERSION} > 900007
BROKEN=		fails to build with new utmpx
.endif

.include <bsd.port.post.mk>

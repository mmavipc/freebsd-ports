# Created by: Seiya Yanagita <s_yanagita@ybb.ne.jp>
# $FreeBSD$

PORTNAME=	scim-uim
PORTVERSION=	0.2.0
PORTREVISION=	7
CATEGORIES=	japanese
MASTER_SITES=	SF/scim/${PORTNAME}/${PORTVERSION} \
		http://freedesktop.org/~suzhe/sources/


MAINTAINER=	s_yanagita@ybb.ne.jp
COMMENT=	SCIM IMEngine module using UIM input method library

BUILD_DEPENDS=	scim:${PORTSDIR}/textproc/scim
LIB_DEPENDS=	uim:${PORTSDIR}/textproc/uim
RUN_DEPENDS:=	${BUILD_DEPENDS}

USE_GNOME=	lthack
USES=		gmake iconv pkgconfig
GNU_CONFIGURE=	yes

CONFIGURE_ENV=	PTHREAD_CFLAGS="${PTHREAD_CFLAGS}" \
		PTHREAD_LIBS="${PTHREAD_LIBS}"

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

NO_STAGE=	yes
post-install:
	@${CAT} ${PKGMESSAGE}
	@${ECHO}
	@${ECHO} To display this message again, type \`pkg_info -D ${PKGNAME}\'
	@${ECHO}

.include <bsd.port.mk>

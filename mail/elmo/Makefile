# Created by: trevor
# $FreeBSD$

PORTNAME=	elmo
PORTVERSION=	1.3.0
PORTREVISION=	3
CATEGORIES=	mail
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}-${PORTVERSION}

MAINTAINER=	dhn@FreeBSD.org
COMMENT=	Receive, filter, read, compose, and send mail at the text console

CONFLICTS=	elmo-devel-[0-9]*

OPTIONS_DEFINE=	NLS

GNU_CONFIGURE=	yes
USES=		iconv shebangfix perl5
USE_OPENSSL=	yes
USE_PERL5=	run
SHEBANG_FILES=	src/elmoconf.pl

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/COPYING

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

MAN1=		elmo.1 elmoconf.pl.1

NLS_CONFIGURE_ON=	--with-libintl-prefix="${LOCALBASE}"
NLS_CONFIGURE_OFF=	--disable-nls
NLS_USES=	gettext
OPTIONS_SUB=	yes

.if exists(${LOCALBASE}/lib/libgpgme.so) || defined(WITH_GPGME)
LIB_DEPENDS+=	libgpgme.so:${PORTSDIR}/security/gpgme
.else
NO_STAGE=	yes
pre-everything::
	@${ECHO_CMD}
	@${ECHO_CMD} "Define WITH_GPGME=yes to build with gpgme support."
	@${ECHO_CMD}
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|gpgme4|gpgme|g' -e 's|== "|= "|g' ${WRKSRC}/configure
	@${REINPLACE_CMD} -e 's|gpgme4|gpgme|g' ${WRKSRC}/src/pgp.c

post-install:
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>

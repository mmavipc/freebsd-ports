# Created by: Alex Dupre <ale@FreeBSD.org>
# $FreeBSD$

PORTNAME=	pam_p11
PORTVERSION=	0.1.5
PORTREVISION=	3
CATEGORIES=	security
MASTER_SITES=	http://www.opensc-project.org/files/${PORTNAME}/

MAINTAINER=	ale@FreeBSD.org
COMMENT=	A PAM module using crypto tokens for auth

LIB_DEPENDS=	p11.2:${PORTSDIR}/security/libp11

USE_AUTOTOOLS=	libtool
USE_OPENSSL=	yes
GNU_CONFIGURE=	yes
USES=		pkgconfig
NO_STAGE=	yes

CONFIGURE_ENV=	OPENSSL_CFLAGS="-I${OPENSSLINC}" \
		OPENSSL_LIBS="-L${OPENSSLLIB} -lssl"

PORTDOCS=	*

.ifndef(NOPORTDOCS)
post-install:
	@${MKDIR} ${DOCSDIR}/wiki
	@(cd ${WRKSRC} && ${CP} NEWS ${DOCSDIR})
	@(cd ${WRKSRC}/doc && ${CP} README ${DOCSDIR})
	@(cd ${WRKSRC}/doc && ${CP} *.css *.html ${DOCSDIR}/wiki)
.endif

.include <bsd.port.mk>

# Created by: chinsan
# $FreeBSD$

PORTNAME=	Text-QRCode
PORTVERSION=	0.02
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Generate text based QR Code

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

LIB_DEPENDS=	libqrencode.so:${PORTSDIR}/graphics/libqrencode

MAKE_ARGS=	PKG_CONFIG_PATH=${LOCALBASE}/bin
USES=		perl5 pkgconfig
USE_PERL5=	configure

post-patch:
	@${REINPLACE_CMD} -e 's|qrencode.h|${LOCALBASE}/include/&|' ${WRKSRC}/Makefile.PL ${WRKSRC}/QRCode.xs

.include <bsd.port.mk>

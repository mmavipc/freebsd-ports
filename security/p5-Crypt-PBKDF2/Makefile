# Created by: Victor Popov <v.a.popov@gmail.com>
# $FreeBSD$

PORTNAME=	Crypt-PBKDF2
PORTVERSION=	0.133330
CATEGORIES=	security perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:ARODLAND
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	The PBKDF2 password hashing algorithm

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-Digest-HMAC>=1.01:${PORTSDIR}/security/p5-Digest-HMAC \
		p5-Method-Signatures-Simple>=0:${PORTSDIR}/devel/p5-Method-Signatures-Simple \
		p5-Module-Runtime>=0:${PORTSDIR}/devel/p5-Module-Runtime \
		p5-Moose>=1:${PORTSDIR}/devel/p5-Moose \
		p5-Try-Tiny>=0.04:${PORTSDIR}/lang/p5-Try-Tiny \
		p5-namespace-autoclean>=0:${PORTSDIR}/devel/p5-namespace-autoclean
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>

# Created by: Jin-Shan Tseng <tjs@cdpa.nsysu.edu.tw>
# $FreeBSD$

PORTNAME=	Math-Random-OO
PORTVERSION=	0.21
CATEGORIES=	math perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Consistent object-oriented interface for generating random numbers

BUILD_DEPENDS=	p5-Test-MockRandom>=0.95:${PORTSDIR}/devel/p5-Test-MockRandom \
		p5-Test-Number-Delta>=0.14:${PORTSDIR}/devel/p5-Test-Number-Delta
RUN_DEPENDS=	p5-Class-Accessor>=0.18:${PORTSDIR}/devel/p5-Class-Accessor \
		p5-Params-Validate>=0.76:${PORTSDIR}/devel/p5-Params-Validate

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>

# Created by: kftseng@iyard.org
# $FreeBSD$

PORTNAME=	HTML-StripScripts-Parser
PORTVERSION=	1.03
CATEGORIES=	www perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	ports@FreeBSD.org
COMMENT=	XSS filter using HTML::Parser

BUILD_DEPENDS=	p5-HTML-Parser>=3.56:${PORTSDIR}/www/p5-HTML-Parser \
		p5-HTML-StripScripts>=1.05:${PORTSDIR}/www/p5-HTML-StripScripts
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>

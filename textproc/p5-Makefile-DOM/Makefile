# Created by: Gea-Suan Lin <gslin@gslin.org>
# $FreeBSD$

PORTNAME=	Makefile-DOM
PORTVERSION=	0.006
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:AGENT
PKGNAMEPREFIX=	p5-

MAINTAINER=	gslin@gslin.org
COMMENT=	Simple DOM parser for Makefiles

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

RUN_DEPENDS=	p5-Clone>=0.18:${PORTSDIR}/devel/p5-Clone \
		p5-List-MoreUtils>=0.21:${PORTSDIR}/lang/p5-List-MoreUtils \
		p5-Params-Util>=0.22:${PORTSDIR}/devel/p5-Params-Util

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>

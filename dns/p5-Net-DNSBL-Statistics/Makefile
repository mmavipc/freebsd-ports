# Created by: Jin-Shan Tseng <tjs@cdpa.nsysu.edu.tw>
# $FreeBSD$

PORTNAME=	Net-DNSBL-Statistics
PORTVERSION=	0.12
CATEGORIES=	dns mail perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Gather DNSBL Statistics

RUN_DEPENDS=	p5-Net-DNS-Codes>=0.09:${PORTSDIR}/dns/p5-Net-DNS-Codes \
		p5-Net-DNS-ToolKit>=0.35:${PORTSDIR}/dns/p5-Net-DNS-ToolKit \
		p5-Net-DNSBL-MultiDaemon>=0.22:${PORTSDIR}/dns/p5-Net-DNSBL-MultiDaemon
BUILD_DEPENDS=	p5-Net-DNS-Codes>=0.09:${PORTSDIR}/dns/p5-Net-DNS-Codes \
		p5-Net-DNS-ToolKit>=0.35:${PORTSDIR}/dns/p5-Net-DNS-ToolKit \
		p5-Net-DNSBL-MultiDaemon>=0.22:${PORTSDIR}/dns/p5-Net-DNSBL-MultiDaemon

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>

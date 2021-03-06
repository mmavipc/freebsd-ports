# Created by: toni.viemero@iki.fi
# $FreeBSD$

PORTNAME=	W3C-LogValidator
PORTVERSION=	1.4
PORTEPOCH=	1
CATEGORIES=	www perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	toni.viemero@iki.fi
COMMENT=	A comprehensive validation tool for webmasters and web developers

BUILD_DEPENDS=	p5-libwww>=0:${PORTSDIR}/www/p5-libwww \
		p5-URI>=0:${PORTSDIR}/net/p5-URI \
		p5-Config-General>=0:${PORTSDIR}/devel/p5-Config-General \
		p5-Mail-Sendmail>=0:${PORTSDIR}/mail/p5-Mail-Sendmail \
		p5-WebService-Validator-CSS-W3C>=0:${PORTSDIR}/www/p5-webservice-validator-css-w3c \
		p5-WebService-Validator-HTML-W3C>=0:${PORTSDIR}/www/p5-webservice-validator-html-w3c \
		${LOCALBASE}/bin/checklink:${PORTSDIR}/www/p5-W3C-LinkChecker
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	W3C::LogValidator.3 \
	W3C::LogValidator::Basic.3 \
	W3C::LogValidator::CSSValidator.3 \
	W3C::LogValidator::Config.3 \
	W3C::LogValidator::HTMLValidator.3 \
	W3C::LogValidator::Output::HTML.3 \
	W3C::LogValidator::Output::Mail.3 \
	W3C::LogValidator::Output::Raw.3 \
	W3C::LogValidator::SurveyEngine.3

NO_STAGE=	yes
post-install:
.ifndef (NOPORTEXAMPLES)
	@${MKDIR} ${EXAMPLESDIR}/
	@${INSTALL_DATA} ${WRKSRC}/samples/NewModule.pm ${EXAMPLESDIR}/
	@${INSTALL_DATA} ${WRKSRC}/samples/NewOutputModule.pm ${EXAMPLESDIR}/
	@${INSTALL_DATA} ${WRKSRC}/samples/logprocess.conf ${EXAMPLESDIR}/
.endif

.include <bsd.port.mk>

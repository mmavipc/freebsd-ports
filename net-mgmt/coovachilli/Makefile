# Created by: Sevan Janiyan <venture37@geeklan.co.uk>
# $FreeBSD$

PORTNAME=	coovachilli
PORTVERSION=	1.0.12
PORTREVISION=	1
CATEGORIES=	net-mgmt
MASTER_SITES=	http://ap.coova.org/chilli/ \
		http://www.geeklan.co.uk/files/ \
		http://www.venture37.com/files/
DISTNAME=	coova-chilli-${PORTVERSION}

MAINTAINER=	venture37@geeklan.co.uk
COMMENT=	An access controller for wired & wireless clients

CONFLICTS=	chillispot-[0-9]*

MAN1=		chilli_query.1 chilli_radconfig.1 chilli_response.1
MAN5=		chilli.conf.5 chilli-radius.5
MAN8=		chilli.8

CONFIGURE_ARGS=-localstatedir=/var
GNU_CONFIGURE=	yes
USES=		perl5
USE_PERL5=	build
USE_LDCONFIG=	yes
USE_RC_SUBR=	coovachilli

NO_STAGE=	yes
post-install:
.if !defined(NOPORTEXAMPLES)
	${MKDIR} ${EXAMPLESDIR}
	${INSTALL_MAN} ${FILESDIR}/main.conf.sample ${EXAMPLESDIR}
	${INSTALL_MAN} ${FILESDIR}/pf.conf.sample ${EXAMPLESDIR}
	${INSTALL_MAN} ${FILESDIR}/ipfw-config.sample ${EXAMPLESDIR}
.endif
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>

# Created by: Christer Edwards <christer.edwards@gmail.com>
# $FreeBSD$

PORTNAME=	listadmin
PORTVERSION=	2.40
CATEGORIES=	mail perl5
MASTER_SITES=	http://heim.ifi.uio.no/kjetilho/hacks/

MAINTAINER=	christer.edwards@gmail.com
COMMENT=	Command-line alternative to Mailman Web interface

RUN_DEPENDS=	p5-Text-Reform>=0:${PORTSDIR}/textproc/p5-Text-Reform \
		p5-HTML-Parser>=0:${PORTSDIR}/www/p5-HTML-Parser \
		p5-Crypt-SSLeay>=0:${PORTSDIR}/security/p5-Crypt-SSLeay \
		p5-libwww>=0:${PORTSDIR}/www/p5-libwww

USES=		perl5
USE_PERL5=	run

PLIST_FILES=	bin/listadmin
MAN1=		listadmin.1

NO_STAGE=	yes
do-install:
	@${INSTALL_SCRIPT} ${WRKSRC}/listadmin.pl ${PREFIX}/bin/listadmin
	@${INSTALL_MAN} ${WRKSRC}/listadmin.man ${MAN1PREFIX}/man/man1/listadmin.1

.include <bsd.port.mk>

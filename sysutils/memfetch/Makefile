# Created by: Yonatan <onatan@gmail.com>
# $FreeBSD$

PORTNAME=	memfetch
PORTVERSION=	0.05b
CATEGORIES=	sysutils
MASTER_SITES=	http://lcamtuf.coredump.cx/soft/
DISTNAME=	${PORTNAME}
EXTRACT_SUFX=	.tgz

MAINTAINER=	onatan@gmail.com
COMMENT=	Utility to dump memory of a running process

LICENSE=	GPLv2

USES=		perl5
USE_PERL5=	run
MAKE_ARGS=	CC="${CC}" CFLAGS="${CFLAGS}"

WRKSRC=		${WRKDIR}/${PORTNAME}

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin
	${INSTALL_SCRIPT} ${WRKSRC}/mffind.pl ${STAGEDIR}${PREFIX}/bin
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>

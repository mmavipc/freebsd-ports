# Created by: Kris Kennaway <kris@FreeBSD.org>
# $FreeBSD$

PORTNAME=	cowsay
PORTVERSION=	3.03
PORTREVISION=	1
CATEGORIES=	games
MASTER_SITES=	http://www.nog.net/~tony/warez/

MAINTAINER=	wxs@FreeBSD.org
COMMENT=	Configurable talking characters in ASCII art

USES=		perl5

NO_BUILD=	# defined

MAN1=		cowsay.1
MLINKS=		cowsay.1 cowthink.1

.if defined(MAINTAINER_MODE)
DISTFILES+=	${DISTNAME}${EXTRACT_SUFX}.sig
verify: fetch
	@${ECHO_MSG} "Checking ${DISTNAME}${EXTRACT_SUFX}"
	@gpg --verify ${DISTDIR}/${DISTNAME}${EXTRACT_SUFX}.sig 2>/dev/null || echo "Bad signature!"
	@${ECHO_MSG} "Done"
.endif

NO_STAGE=	yes
do-install:
	cd ${WRKSRC}; ${SH} install.sh ${PREFIX}
	@${INSTALL_DATA} ${FILESDIR}/box.cow ${PREFIX}/share/cows
	@${INSTALL_DATA} ${FILESDIR}/jkh.cow ${PREFIX}/share/cows
	@${INSTALL_DATA} ${FILESDIR}/tux-stab.cow ${PREFIX}/share/cows

.include <bsd.port.mk>

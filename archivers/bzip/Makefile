# Created by: Andreas Klemm <andreas@klemm.gtn.com>
# $FreeBSD$

PORTNAME=	bzip
PORTVERSION=	0.21
CATEGORIES=	archivers
MASTER_SITES=	http://ftp.riken.jp/FreeBSD/distfiles/RESTRICTED/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Block-sorting file compressor

RESTRICTED=	may be covered by patents
USE_CSTD=	gnu89

PLIST_FILES=	bin/bzip bin/bunzip \
		man/man1/bzip.1.gz \
		man/man1/bunzip.1.gz

pre-install:
	@${CAT} ${FILESDIR}/COPYRIGHT

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/bzip ${STAGEDIR}${PREFIX}/bin
	${LN} -fs bzip ${STAGEDIR}${PREFIX}/bin/bunzip
	${INSTALL_MAN} ${WRKSRC}/bzip.1 ${STAGEDIR}${MAN1PREFIX}/man/man1/bzip.1
	${INSTALL_MAN} ${WRKSRC}/bzip.1 ${STAGEDIR}${MAN1PREFIX}/man/man1/bunzip.1

.include <bsd.port.mk>

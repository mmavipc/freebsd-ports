# Created by: Michael Johnson <ahze@ahze.net>
# $FreeBSD$

PORTNAME=	estraier
PORTVERSION=	1.2.30
PORTREVISION=	1
CATEGORIES=	textproc
MASTER_SITES=	http://fallabs.com/estraier/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	A full-text search system for personal use

LIB_DEPENDS=	libqdbm.so:${PORTSDIR}/databases/qdbm

OPTIONS_DEFINE=	CHASEN MECAB KAKASI
OPTIONS_DEFAULT=	KAKASI
CHASEN_DESC=	Japanese Morphological Analysis Support
MECAB_DESC=	Part-of-Speech and Morphological Analyzer
KAKASI_DESC=	Language processing filter/converter

USES=		iconv
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-sysqdbm \
		--enable-dlfilter \
		--enable-devel
CPPFLAGS+=	-I${LOCALBASE}/include ${PTHREAD_CFLAGS}
LDFLAGS+=	-L${LOCALBASE}/include ${PTHREAD_LIBS}

CHASEN_LIB_DEPENDS=	libchasen.so:${PORTSDIR}/japanese/chasen-base
CHASEN_CONFIGURE_ENABLE=	chasen

KAKASI_LIB_DEPENDS=	libkakasi.so:${PORTSDIR}/japanese/kakasi
KAKASI_CONFIGURE_ENABLE=	kakasi

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MMECAB} && ${ARCH} == "i386"
LIB_DEPENDS+=	libmecab.so:${PORTSDIR}/japanese/mecab
CONFIGURE_ARGS+=	--enable-mecab
.endif

post-patch:
	@${REINPLACE_CMD} -e \
		's|-lc ||g' ${WRKSRC}/configure
	@${REINPLACE_CMD} -e \
		's|-O2|@CFLAGS@|g ; \
		 s|HOME|LOCALBASE|g ; \
		 s|:/usr/local/lib||g ; \
		 s|-I/usr/local/include|${PTHREAD_CFLAGS}|g ; \
		 s|-L/usr/local/lib|${PTHREAD_LIBS}|g' ${WRKSRC}/Makefile.in

post-install:
.for file in estindex estmbtomh estserver estsiutil estxview
	@${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/${file}
.endfor

.include <bsd.port.mk>

# Created by: siasia
# $FreeBSD$

PORTNAME=	v8
PORTVERSION=	3.24.7
CATEGORIES=	lang
MASTER_SITES=	LOCAL/vanilla
PKGNAMESUFFIX=	-devel

MAINTAINER=	vanilla@FreeBSD.org
COMMENT=	Google\'s open source JavaScript engine

BUILD_DEPENDS=	python:${PORTSDIR}/lang/python
LIB_DEPENDS=	libexecinfo.so:${PORTSDIR}/devel/libexecinfo \
		libicui18n.so:${PORTSDIR}/devel/icu

CONFLICTS=	v8-3.19.*

USES=		gmake shebangfix
SHEBANG_LANG=	sh
SHEBANG_FILES=	${WRKSRC}/build/gyp/gyp
USE_XZ=		yes
USE_PYTHON=	2
USE_LDCONFIG=	yes
ALL_TARGET=	native
MAKE_ARGS=	library=shared use_system_icu=on
MAKE_ENV+=	CC.host=${CC} CXX.host=${CXX} LINK.host=${CXX} LINK.target=${CXX}
sh_OLD_CMD=	/bin/bash
sh_CMD=		${SH}

.include <bsd.port.pre.mk>

.if ${CC:T:Mclang} == "clang" || ${CXX:T:Mclang++} == "clang++" || ${OSVERSION} >= 1000024
_CLANG!=	${CC} --version | ${HEAD} -1 | ${SED} -e 's/.*clang version \([0-9]\)\.\([0-9]\).*/\1\2/'
MAKE_ENV+=	LINK=clang++ AR=/usr/bin/ar
MAKE_ARGS+=	clang=on
CFLAGS+=	-Wno-unused-private-field -Wno-unused-variable
.if ${_CLANG} >= 33
CFLAGS+=	-Wno-nested-anon-types -Wno-unused-function
.endif
.else
MAKE_ARGS+=	strictaliasing=off
USE_GCC=	any
.endif

ONLY_FOR_ARCHS=	i386 amd64

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/out/native/d8 ${STAGEDIR}${PREFIX}/bin/d8
	${INSTALL_LIB} -m 755 ${WRKSRC}/out/native/lib.target/libv8.so ${STAGEDIR}${PREFIX}/lib/libv8.so.1
	${LN} -sf ${PREFIX}/lib/libv8.so.1 ${STAGEDIR}${PREFIX}/lib/libv8.so
	${INSTALL_DATA} ${WRKSRC}/include/v8.h ${STAGEDIR}${PREFIX}/include
	${INSTALL_DATA} ${WRKSRC}/include/v8-debug.h ${STAGEDIR}${PREFIX}/include
	${INSTALL_DATA} ${WRKSRC}/include/v8-platform.h ${STAGEDIR}${PREFIX}/include
	${INSTALL_DATA} ${WRKSRC}/include/v8-profiler.h ${STAGEDIR}${PREFIX}/include
	${INSTALL_DATA} ${WRKSRC}/include/v8-testing.h ${STAGEDIR}${PREFIX}/include
	${INSTALL_DATA} ${WRKSRC}/include/v8config.h ${STAGEDIR}${PREFIX}/include
	${INSTALL_DATA} ${WRKSRC}/include/v8stdint.h ${STAGEDIR}${PREFIX}/include

.include <bsd.port.post.mk>

# Created by: Marcin Cieslak <saper@SYSTEM.PL>
# $FreeBSD$

PORTNAME=	tn5250j
PORTVERSION=	0.6.0
PORTREVISION=	3
CATEGORIES=	net java
MASTER_SITES=	SF
DISTNAME=	${PORTNAME}-${PORTVERSION}-src

MAINTAINER=	saper@saper.info
COMMENT=	A 5250 terminal emulator for the AS/400 written in Java

BUILD_DEPENDS=	${JAVAJARDIR}/mail.jar:${PORTSDIR}/java/javamail \
		${JYTHON_JAR}:${PORTSDIR}/lang/jython \
		${JAVAJARDIR}/jt400.jar:${PORTSDIR}/sysutils/jtopen \
		${JAVAJARDIR}/itext.jar:${PORTSDIR}/devel/itext \
		${JAVAJARDIR}/log4j.jar:${PORTSDIR}/devel/log4j
RUN_DEPENDS=	${JAVAJARDIR}/mail.jar:${PORTSDIR}/java/javamail \
		${JYTHON_JAR}:${PORTSDIR}/lang/jython \
		${JAVAJARDIR}/jt400.jar:${PORTSDIR}/sysutils/jtopen \
		${JAVAJARDIR}/itext.jar:${PORTSDIR}/devel/itext \
		${JAVAJARDIR}/log4j.jar:${PORTSDIR}/devel/log4j

USE_ZIP=	yes
USE_ANT=	yes
USE_JAVA=	1.3+
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}
USE_DOS2UNIX=	build.xml

ALL_TARGET=	package
MAKE_ENV+=	CLASSPATH=${JYTHON_PREFIX}
MAKE_ARGS+=	-Dlib.dir=${JAVALIBDIR}

JYTHON_PREFIX=	${LOCALBASE}/lib/jython
JYTHON_JAR=	${JYTHON_PREFIX}/jython.jar

DOC_FILES=	CHANGELOG.txt applet.txt filetransfers.txt readme.txt antbuild.txt\
		 e-mail.txt macros.txt scripting.txt

SUB_FILES=	tn5250j
SUB_LIST=	JYTHON_JAR=${JYTHON_JAR}

NO_STAGE=	yes
.include <bsd.port.pre.mk>

do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/tn5250j ${PREFIX}/bin
	${INSTALL_DATA} ${WRKSRC}/build/tn5250j.jar ${JAVAJARDIR}

post-install:
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
.for d in ${DOC_FILES}
	${INSTALL_MAN} ${WRKSRC}/src/${d} ${DOCSDIR}
.endfor
.endif

.include <bsd.port.post.mk>

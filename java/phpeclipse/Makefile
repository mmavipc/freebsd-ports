# Created by: rtdean@cytherianage.net
# $FreeBSD$

PORTNAME=	phpeclipse
PORTVERSION=	1.2.3
PORTREVISION=	5
CATEGORIES=	java editors devel
MASTER_SITES=	SF/${PORTNAME}/a%29%20Eclipse%203.3.x/PHPEclipse-${PORTVERSION}
DISTNAME=	PHPEclipse-${PLIST_VER}-src

MAINTAINER=	kamikaze@bsdforen.de
COMMENT=	PHP Eclipse adds PHP support to the Eclipse IDE Framework

BUILD_DEPENDS+=	unzip:${PORTSDIR}/archivers/unzip
RUN_DEPENDS=	eclipse:${PORTSDIR}/java/eclipse

PLUGIN_PATHS=	features plugins
PATCH_TASKS=	eclipse.versionReplacer eclipse.idReplacer

USE_JAVA=	yes
USE_ANT=	yes
USE_ZIP=	yes

WRKSRC=		${WRKDIR}/dist
ECLIPSE=	lib/eclipse
PLIST_VER=	${PORTVERSION}.200910091456PRD

PLIST_SUB=	VER=${PLIST_VER} \
		ECLIPSE=${ECLIPSE}

NO_STAGE=	yes
post-patch:
.for _task in ${PATCH_TASKS}
	@${FIND} ${WRKDIR} -name build.xml -exec ${REINPLACE_CMD} -E \
		-e 's|<(${_task})(.*)/>|<!--\1\2/-->|1' \{} \;
.endfor

do-build:
	@cd ${WRKDIR}/features; \
	for feature in `ls`; do \
		cd "$$feature"; \
		${ANT} zip.distribution; \
		cd ..; \
	done
	@${MKDIR} ${WRKSRC}
	@for file in ${WRKDIR}/features/*/*.zip; do \
		${UNZIP_CMD} "$$file" -d "${WRKSRC}/" ; \
	done

do-install:
.for _path in ${PLUGIN_PATHS}
	@${MKDIR} ${PREFIX}/${ECLIPSE}/${_path}
	@${CP} -r ${WRKSRC}/${_path}/* ${PREFIX}/${ECLIPSE}/${_path}/
.endfor

plist: build
	@${ECHO} "===>  Rebuilding PLIST."
	@${TOUCH} ${PLIST}
	@${RM} ${PLIST}
.for _path in ${PLUGIN_PATHS}
	@${FIND} ${WRKSRC}/${_path}/ -not -type d \
		| ${SED} "s|${WRKSRC}|%%ECLIPSE%%|1" \
		| ${SED} "s|${PLIST_VER}|%%VER%%|g" \
		>> ${PLIST}
	@${FIND} -d ${WRKSRC}/${_path}/ -mindepth 1 -type d \
		| ${SED} "s|${WRKSRC}|@dirrm %%ECLIPSE%%|1" \
		| ${SED} "s|${PLIST_VER}|%%VER%%|g" \
		>> ${PLIST}
	@${ECHO} "@dirrmtry ${ECLIPSE}/${_path}" >> ${PLIST}
.endfor
	@${ECHO} "@dirrmtry ${ECLIPSE}" >> ${PLIST}

post-install:
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>

# Created by: Alexey Dokuchaev <danfe@FreeBSD.org>
# $FreeBSD$

PORTNAME=	pwytter
PORTVERSION=	0.8
PORTREVISION=	2
CATEGORIES=	net-im www python
MASTER_SITES=	GOOGLE_CODE
DISTNAME=	${PORTNAME}-${PORTVERSION}-src

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Free multi-platform Twitter client written in Python

LICENSE=	GPLv2

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}tkinter>0:${PORTSDIR}/x11-toolkits/py-tkinter \
		${PYTHON_SITELIBDIR}/PIL/_imaging.so:${PORTSDIR}/graphics/py-imaging \
		${PYTHON_PKGNAMEPREFIX}simplejson>=1.7.1:${PORTSDIR}/devel/py-simplejson

RUN_DEPENDS:=	${BUILD_DEPENDS}

USE_ZIP=	yes
USES=		gettext
USE_PYTHON=	2
USE_PYDISTUTILS=	easy_install
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

post-patch: .SILENT
	${RM} -r ${WRKSRC}/twclient/simplejson
# Prefer system-wide `simplejson' module; fix for broken `setup.py': include
# `pwCache.py' in sources list, adjust locale data path
	${REINPLACE_CMD} -e "s|'simplejson|}, #&|" \
		-e "s|pwParam|pwCache','&|" ${WRKSRC}/setup.py
	${REINPLACE_CMD} -e 's|locale_path =|& "${PYEASYINSTALL_SITELIBDIR}/${PYEASYINSTALL_EGG}/locale" #|' \
		${WRKSRC}/pwytter.py
# Adjust paths for themes and media (don't assume they are relative to .)
	${REINPLACE_CMD} -e 's|media"|${DATADIR}/&|' ${WRKSRC}/pwytter.py \
		${WRKSRC}/twclient/__init__.py
	${REINPLACE_CMD} -e "s|theme'|${DATADIR}/&|" ${WRKSRC}/pwTheme.py
# Remove gettext `.po' files: not needed when we have them precompiled
	${FIND} ${WRKSRC}/locale -name pwytter.po -delete

NO_STAGE=	yes
post-install:
# Install themes and media files where they belong
	@${MKDIR} ${DATADIR}/media ${DATADIR}/theme
	${INSTALL_DATA} ${WRKSRC}/media/* ${DATADIR}/media
	${INSTALL_DATA} ${WRKSRC}/theme/* ${DATADIR}/theme

.include <bsd.port.mk>

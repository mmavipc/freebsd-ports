# Created by: Daniel Nebdal <dnebdal@gmail.com>
# $FreeBSD$

PORTNAME=	bangarang
PORTVERSION=	2.1
PORTREVISION=	2
CATEGORIES=	multimedia kde
MASTER_SITES=	${MASTER_SITE_GOOGLE_CODE}

MAINTAINER=	dnebdal@gmail.com
COMMENT=	Media player for KDE 4

LICENSE=	GPLv3

LIB_DEPENDS=	tag.1:${PORTSDIR}/audio/taglib

PROJECTHOST=	bangarangissuetracking
USES=		cmake:outsource gettext
USE_QT4=	qmake_build moc_build rcc_build uic_build \
		corelib gui phonon
USE_KDE4=	automoc4 kdelibs kdeprefix


WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTNAME}

NO_STAGE=	yes
.include <bsd.port.mk>

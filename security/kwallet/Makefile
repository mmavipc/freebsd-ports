# Created by: Martin Wilke <miwi@FreeBSD.org>
# $FreeBSD$

PORTNAME=	kwallet
PORTVERSION=	${KDE4_VERSION}
CATEGORIES=	security kde
MASTER_SITES=	${MASTER_SITE_KDE}
MASTER_SITE_SUBDIR=	${KDE4_BRANCH}/${PORTVERSION}/src
DIST_SUBDIR=	KDE/${PORTVERSION}

MAINTAINER=	kde@FreeBSD.org
COMMENT=	Password manager for KDE

CONFLICTS_INSTALL=	kdeutils-4.[0-7].*

USE_XZ=		yes
USE_KDE4=	kdeprefix kdehier automoc4 kdelibs
USES=		cmake:outsource
USE_QT4=	qmake_build moc_build rcc_build uic_build

NO_STAGE=	yes
.include <bsd.port.mk>

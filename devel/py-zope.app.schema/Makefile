# $FreeBSD$

PORTNAME=	zope.app.schema
PORTVERSION=	3.5.0
CATEGORIES=	devel python zope
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	zope@FreeBSD.org
COMMENT=	Component Architecture based Vocabulary Registry

LICENSE=	ZPL21

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}zope.component>=0:${PORTSDIR}/devel/py-zope.component \
		${PYTHON_PKGNAMEPREFIX}zope.interface>=0:${PORTSDIR}/devel/py-zope.interface \
		${PYTHON_PKGNAMEPREFIX}zope.schema>=0:${PORTSDIR}/devel/py-zope.schema

DIST_SUBDIR=	zope
USE_PYTHON=	yes
USE_PYDISTUTILS=easy_install

NO_STAGE=	yes

.include <bsd.port.mk>

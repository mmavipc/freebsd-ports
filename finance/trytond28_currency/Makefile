# Created by: Matthias Petermann <matthias@petermann-it.de>
# $FreeBSD$

PORTNAME=	trytond28_currency
PORTVERSION=	2.8.0
CATEGORIES=	finance python
MASTER_SITES=	https://pypi.python.org/packages/source/t/trytond_currency/ \
		http://downloads.tryton.org/${PORTVERSION:R}/
DISTNAME=	trytond_currency-${PORTVERSION}

MAINTAINER=	matthias@petermann-it.de
COMMENT=	Tryton Application Platform (Currency Module)

LICENSE=	GPLv3

RUN_DEPENDS=	trytond28>=2.8.2:${PORTSDIR}/finance/trytond28

CONFLICTS=	trytond_currency-2.[46].*

USE_PYTHON=	yes
USE_PYDISTUTILS=easy_install
PYEASYINSTALL_EGG=${DISTNAME}-py${PYTHON_VER}${PYEASYINSTALL_OSARCH}.egg

.include <bsd.port.mk>

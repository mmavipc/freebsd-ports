# Created by: Alexey V. Degtyarev <alexey@renatasystems.org>
# $FreeBSD$

PORTNAME=	botocore
PORTVERSION=	0.28.0
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	alexey@renatasystems.org
COMMENT=	Low-level, core functionality of boto 3

LICENSE=	MIT

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}dateutil>=2.1:${PORTSDIR}/devel/py-dateutil \
		${PYTHON_PKGNAMEPREFIX}jmespath>=0.2.0:${PORTSDIR}/devel/py-jmespath \
		${PYTHON_PKGNAMEPREFIX}six>=1.1.0:${PORTSDIR}/devel/py-six

USE_PYTHON=	yes
USE_PYDISTUTILS=yes
PYDISTUTILS_AUTOPLIST=	yes

.include <bsd.port.mk>

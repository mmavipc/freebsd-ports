# Created by: ijliao
# $FreeBSD$

PORTNAME=	jabber
PORTVERSION=	0.5
CATEGORIES=	net-im python
MASTER_SITES=	SF/${PORTNAME}py/${PORTNAME}py%20libs/${PORTVERSION}
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	jabberpy-${PORTVERSION}-0

MAINTAINER=	flz@FreeBSD.org
COMMENT=	A Python Jabber library

USE_PYTHON=	yes
USE_PYDISTUTILS=	yes
PYDISTUTILS_PKGNAME=	jabber.py
PYDISTUTILS_PKGVERSION=	0.3-1

NO_STAGE=	yes
post-install:
	@${ECHO} "jabber" > ${PYTHON_SITELIBDIR}/jabber.pth

.include <bsd.port.mk>

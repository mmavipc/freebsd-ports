# Created by: Jin-Sih Lin <linpct@gmail.com>
# $FreeBSD$

PORTNAME=	ranger
PORTVERSION=	1.6.1
CATEGORIES=	sysutils python
MASTER_SITES=	http://ranger.nongnu.org/
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	linpct@gmail.com
COMMENT=	Ranger is a file manager with VI key bindings

USE_PYTHON=	yes
USE_PYDISTUTILS=	yes

MAN1=		ranger.1 rifle.1

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e 's|setuptools|distutils.core|; s|share/man/man|man/man|;s|share/doc|doc|' ${WRKSRC}/${PYSETUP}

.include <bsd.port.mk>

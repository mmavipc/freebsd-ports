# Created by: Ion-Mihai "IOnut" Tetcu <itetcu@FreeBSD.org>
# $FreeBSD$

PORTNAME=	user_special_mailboxes
PORTVERSION=	0.1
PORTREVISION=	2
CATEGORIES=		mail www
DISTNAME=	${PORTNAME:S/-/_/}.${PORTVERSION}-1.4

MAINTAINER=	itetcu@FreeBSD.org
COMMENT=	Lets define folders to be displayed at the top of the folders list

USE_SM_COMPAT=	yes

SQUIRREL_PLUGIN_NAME=	${PORTNAME:S/-/_/}

NO_STAGE=	yes

.include <bsd.port.pre.mk>
.include "${.CURDIR}/../squirrelmail/bsd.squirrelmail.mk"
.include <bsd.port.post.mk>

# Created by: Hajimu UMEMOTO <ume@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gkrellm
PORTVERSION=	1.2.13
PORTREVISION=	11
CATEGORIES=	sysutils ipv6
MASTER_SITES=	http://members.dslextreme.com/users/billw/gkrellm/ \
		${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	ume

MAINTAINER=	ume@FreeBSD.org
COMMENT=	A GTK based system monitor

CONFLICTS=	gkrellm-[^1].* gkrellm[^1]-[^1].*

USES=		gettext gmake
USE_BZIP2=	yes
USE_GNOME=	imlib

INCLUDES=	gkrellm.h gkrellm_public_proto.h
MAN1=		gkrellm.1

.if !defined(NOPORTDOCS)
PORTDOCS=	COPYRIGHT README Themes.html
.endif

# If you want to support LM78/79 feature, set this to `yes'.  You
# should aware that GKrellM must be setuid root to obtain
# temperatures.  Furthermore, this causes problem on some
# motherboards.  If your motherboard doesn't support LM78/79 feature,
# you should not enable this.
# WITH_SENSOR=yes

NO_STAGE=	yes
.include <bsd.port.pre.mk>

ALL_TARGET=	freebsd

BINGRP=		kmem
.if defined(WITH_SENSOR)
BINOWN=		root
BINMODE=	4511
.else
BINMODE=	2511
.endif

MAKE_ENV+=	LOCALEDIR=${PREFIX}/share/locale
CFLAGS+=	-DSYSTEM_THEMES_DIR='\"${PREFIX}/share/gkrellm/themes\"' \
		-DSYSTEM_PLUGINS_DIR='\"${PREFIX}/libexec/gkrellm/plugins\"'

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/src/gkrellm ${PREFIX}/bin/gkrellm
	@cd ${WRKSRC}/po && \
		${GMAKE} install enable_nls=1 LOCALEDIR=${PREFIX}/share/locale

	@${MKDIR} ${PREFIX}/include/gkrellm
.for f in ${INCLUDES}
	${INSTALL_DATA} ${WRKSRC}/src/${f} ${PREFIX}/include/gkrellm
.endfor
	@${MKDIR} ${PREFIX}/libexec/gkrellm/plugins
	@${MKDIR} ${PREFIX}/share/gkrellm/themes
.for f in ${MAN1}
	${INSTALL_MAN} ${WRKSRC}/${f} ${MANPREFIX}/man/man1/${f}
.endfor
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
.for f in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${f} ${DOCSDIR}
.endfor
.endif
.if !defined(WITH_SENSOR)
	@${CAT} ${PKGMESSAGE}
.endif

.include <bsd.port.post.mk>

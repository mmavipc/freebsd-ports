# Created by: Rene Ladan <r.c.ladan@student.tue.nl>
# $FreeBSD$

PORTNAME=	coq
PORTVERSION=	8.4.3
PORTEPOCH=	1
CATEGORIES=	math
MASTER_SITES=	http://coq.inria.fr/distrib/V${COQVERSION}/files/ \
		ftp://ftp.stack.nl/pub/users/johans/coq/
DISTNAME=	${PORTNAME}-${COQVERSION}

MAINTAINER=	johans@FreeBSD.org
COMMENT=	Theorem prover based on lambda-C

BUILD_DEPENDS=	camlp5:${PORTSDIR}/devel/ocaml-camlp5 \
		ocamlfind:${PORTSDIR}/devel/ocaml-findlib

COQVERSION=	${PORTVERSION:R}pl${PORTVERSION:E}
USES=		gmake
USE_OCAML=	yes
ALL_TARGET=	world

HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--prefix ${PREFIX} \
		--mandir ${PREFIX}/man \
		--emacslib ${PREFIX}/share/emacs/site-lisp \
		--opt
MAKE_ENV=	COQINSTALLPREFIX=${DESTDIR}

OPTIONS_DEFINE=		DOCS IDE
OPTIONS_DEFAULT=	DOCS IDE
OPTIONS_SUB=		yes
IDE_DESC=		Include desktop environment (coqide)
IDE_BUILD_DEPENDS=	lablgtk2:${PORTSDIR}/x11-toolkits/ocaml-lablgtk2
IDE_RUN_DEPENDS=	${IDE_BUILD_DEPENDS
IDE_CONFIGURE_OFF=	--coqide no
DOCS_USE=		TEX=latex:build,dvipsk:build
DOCS_BUILD_DEPENDS=	hevea:${PORTSDIR}/textproc/hevea \
	${LOCALBASE}/share/texmf/tex/latex/ucs/utf8x.def:${PORTSDIR}/print/latex-ucs
DOCS_CONFIGURE_OFF=	--with-doc none
PORTDOCS=		*

.include <bsd.port.pre.mk>

.if ${ARCH} == "powerpc"
BROKEN=		Does not link on powerpc
.endif

post-patch:
	@${REINPLACE_CMD} -e '/FreeBSD.*\.byte/s/^/#/' \
		-e '1s:/bin/bash:/bin/sh:' \
		-e '/^MAKE=/d' ${WRKSRC}/configure
	@${REINPLACE_CMD} -e 's:/bin/bash:/bin/sh:' \
		${WRKSRC}/Makefile* ${WRKSRC}/install.sh
	@${REINPLACE_CMD} -e '/^#COQINSTALLPREFIX/{s/^#//;s|$$|$${DESTDIR}|;}' \
		${WRKSRC}/Makefile.build
	@${REINPLACE_CMD} -e '/show_latex_mes/s/)$$/; true)/' ${WRKSRC}/Makefile.doc

.include <bsd.port.post.mk>

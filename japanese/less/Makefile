# Created by: Nobuhiro Yasutomi <nobu@psrc.isac.co.jp>
# $FreeBSD$

PORTNAME=	less
PORTVERSION=	382.262
PORTREVISION=	3
CATEGORIES=	japanese
MASTER_SITES=	LOCAL/nork
PKGNAMESUFFIX=	+iso
DISTNAME=	less-${PORTVERSION:R}
DISTFILES=	${DISTNAME}${EXTRACT_SUFX} \
		regex_cs-lwp9k.shar.gz
EXTRACT_ONLY=	${DISTNAME}${EXTRACT_SUFX}

PATCH_SITES=	${MASTER_SITE_LOCAL}
PATCH_SITE_SUBDIR=	nork
PATCHFILES=	${DISTNAME}-iso258.patch.gz \
		${DISTNAME}-iso258-259.patch.gz \
		${DISTNAME}-iso259-260.patch.gz \
		${DISTNAME}-iso260-261.patch.gz \
		${DISTNAME}-iso261-${PORTVERSION:E}.patch.gz \
		${DISTNAME}-iso${PORTVERSION:E}.ext03.patch.gz
PATCH_DIST_STRIP=	-p1

MAINTAINER=	hrs@FreeBSD.org
COMMENT=	Less + zcat + ISO-2022 + UTF-8 - a pager similar to more and pg

LICENSE=	GPLv2

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-cs-regex
PORTDOCS=	README.iso README.iso.jp README.lesw.euc \
		README.regex README.regex.jp README.ext.jp
PLIST_FILES=	bin/jless bin/jlesskey bin/jlessecho

MAN1=		jless.1 jlesskey.1

OPTIONS_DEFINE=	DOCS

NO_STAGE=	yes
.include <bsd.port.options.mk>

post-extract:
	cd ${WRKDIR} && \
		${GZCAT} ${DISTDIR}/regex_cs-lwp9k.shar.gz | ${SH} && \
		${MV} regex_cs.[ch] README.regex README.regex.jp \
			README.lesw.euc ${WRKSRC}

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	cd ${WRKSRC} && ${INSTALL_DATA} ${PORTDOCS} ${DOCSDIR}
.endif

.include <bsd.port.mk>

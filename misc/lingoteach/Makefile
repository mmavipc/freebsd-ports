# $FreeBSD$

PORTNAME=	lingoteach
PORTVERSION=	0.3.9
PORTREVISION=	13
CATEGORIES=	misc
MASTER_SITES=	SF/${PORTNAME}/OldFiles
DISTFILES=	${PORTNAME}-ui-${PORTVERSION}.tar.gz
.if defined(WITH_SOUND)
DISTFILES+=	${PORTNAME}-sound-${SOUNDV}.tar.gz
.endif

MAINTAINER=	ports@FreeBSD.org
COMMENT=	A language teaching program with sound

LIB_DEPENDS=	lingoteach.3:${PORTSDIR}/textproc/liblingoteach

WRKSRC=		${WRKDIR}/${PORTNAME}-ui-${PORTVERSION}

USE_GNOME=	gtk20
GNU_CONFIGURE=	yes
USES=		gmake pkgconfig

CONFIGURE_ENV=	LIBS="-L${LOCALBASE}/lib"
CPPFLAGS+=	-I${LOCALBASE}/include

# sound version
SOUNDV=			0.3.9

.if defined(WITH_DEBUG)
CONFIGURE_ARGS+=	--enable-debug
.endif

.if defined(WITH_SOUND)
PLIST=		${WRKDIR}/plist
.endif

NO_STAGE=	yes
.include <bsd.port.pre.mk>

pre-everything::
	@${ECHO_CMD} ""
	@${ECHO_CMD} "	Available options for lingoteach:"
	@${ECHO_CMD} ""
	@${ECHO_CMD} " 		 WITH_SOUND	download additional sounds"
	@${ECHO_CMD} "				for lingoteach"
	@${ECHO_CMD} " 		 WITH_DEBUG	enable debugging"
	@${ECHO_CMD} ""

post-patch::
.if defined(NOPORTDOCS)
	@${REINPLACE_CMD} -e 's|^SUBDIRS = intl src po data doc|SUBDIRS = src po data|g' \
	    ${WRKSRC}/Makefile.in
.else
	@${REINPLACE_CMD} -e 's|^SUBDIRS = intl src po data doc|SUBDIRS = src po data doc|g' \
	    ${WRKSRC}/Makefile.in
.endif

.if defined(WITH_SOUND)
pre-install::
	@${CAT} pkg-plist | ${SED} '/@dirrm/d' > ${PLIST}; \
	cd ${WRKDIR}/${PORTNAME}-sound-${SOUNDV}/data; \
	${FIND} . -type f \! -name "Make*" | ${CUT} -c2- | \
	${SED} 's|^|${DATADIR:S,${PREFIX}/,,}/data|' \
	| ${SORT} >> ${PLIST}; \
	${CAT} ${.CURDIR}/pkg-plist | ${SED} '/%%PORTDOCS%%@dirrm/!d' >> ${PLIST}; \
	cd ${WRKDIR}/${PORTNAME}-sound-${SOUNDV}/data; \
	${FIND} . -type d | ${CUT} -c2- | ${SED} \
	's|^|@dirrm ${DATADIR:S,${PREFIX}/,,}/data|' | ${SORT} -r >> ${PLIST}; \
	${ECHO_CMD} "@dirrm ${DATADIR:S,${PREFIX}/,,}" >> ${PLIST};
.endif

.if defined(WITH_SOUND)
post-install::
	cd ${WRKDIR}/${PORTNAME}-sound-${SOUNDV}/data; \
	${RM} -f Make*; \
	${CP} -R ${WRKDIR}/${PORTNAME}-sound-${SOUNDV}/data \
	${DATADIR};
.endif

.include <bsd.port.post.mk>

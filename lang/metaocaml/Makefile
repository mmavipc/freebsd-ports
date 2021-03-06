# Created by: Geoffrey Mainland <mainland@apeiron.net>
# $FreeBSD$

PORTNAME=	metaocaml
PORTVERSION=	3.09.a30
PORTREVISION=	2
CATEGORIES=	lang
MASTER_SITES=	http://www.metaocaml.org/dist/old/
DISTNAME=	MetaOCaml_309_alpha_030

MAINTAINER=	mainland@apeiron.net
COMMENT=	The MetaOCaml compiler and programming environment

ONLY_FOR_ARCHS=	i386 amd64 # feel free to test on other archs and send a PR

REINPLACE_ARGS=	-i ""

HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	-prefix ${PREFIX} -cc "${CC} ${CFLAGS}" -with-pthread \
		-libdir ${PREFIX}/lib/metaocaml/lib \
		-bindir ${PREFIX}/lib/metaocaml/bin \
		-mandir ${DATADIR}/man

USE_GMAKE=	yes
ALL_TARGET=	world opt metaocamlopt opt.opt
STRIP=

SUB_FILES=	pkg-message
SUB_LIST=	PORTNAME="${PORTNAME}"

MAN1=		ocamlcp.1 ocamldep.1 ocamldebug.1 ocamldoc.1 ocamlopt.1 \
		ocamlrun.1 ocamlyacc.1 ocamlmktop.1 ocaml.1 ocamlc.1 \
		ocamllex.1 ocamlprof.1 camlp4.1
MANN=		Arg.n Array.n ArrayLabels.n Bigarray.Array1.n \
		Bigarray.Array2.n Bigarray.Array3.n Bigarray.Genarray.n \
		Bigarray.n Buffer.n Callback.n CamlinternalOO.n \
		CamlinternalMod.n Char.n Complex.n Digest.n Filename.n \
		Format.n Gc.n Genlex.n Hashtbl.HashedType.n Hashtbl.Make.n \
		Hashtbl.S.n Hashtbl.n Int32.n Int64.n Lazy.n Lexing.n List.n \
		ListLabels.n Map.Make.n Map.OrderedType.n Map.S.n Map.n \
		Marshal.n MoreLabels.Hashtbl.HashedType.n \
		MoreLabels.Hashtbl.Make.n MoreLabels.Hashtbl.S.n \
		MoreLabels.Hashtbl.n MoreLabels.Map.Make.n \
		MoreLabels.Map.OrderedType.n MoreLabels.Map.S.n \
		MoreLabels.Map.n MoreLabels.Set.Make.n \
		MoreLabels.Set.OrderedType.n MoreLabels.Set.S.n \
		MoreLabels.Set.n MoreLabels.n Nativeint.n Num.n Obj.n Oo.n \
		Parsing.n Pervasives.LargeFile.n Pervasives.n Printexc.n \
		Printf.n Queue.n Random.n Random.State.n Scanf.Scanning.n \
		Scanf.n Set.Make.n Set.OrderedType.n Set.S.n Set.n Sort.n \
		Stack.n StdLabels.Array.n StdLabels.List.n StdLabels.String.n \
		StdLabels.n Str.n Stream.n String.n StringLabels.n Sys.n \
		Unix.LargeFile.n Unix.n Weak.Make.n Weak.S.n Weak.n
MLINKS=		ocamlc.1 ocamlc.opt.1 ocamlopt.1 ocamlopt.opt.1 \
		camlp4.1 camlp4o.1 camlp4.1 camlp4r.1 camlp4.1 mkcamlp4.1 \
		camlp4.1 camlp4o.opt.1 camlp4.1 camlp4r.opt.1 \
		camlp4.1 ocpp.1

OPTIONS_DEFINE=	X11 LABELTK
OPTIONS_DEFAULT=	X11 LABELTK
LABLTK_DESC=	build the LablTk library

PLISTDIR=	${PREFIX}/lib/metaocaml \
		${PREFIX}/share/examples/metaocaml \
		${PREFIX}/bin/metaocaml \
		${PREFIX}/bin/metaocamlc \
		${PREFIX}/bin/metaocamlopt

NO_STAGE=	yes
.include <bsd.port.options.mk>

# Have to set this here and can't use ${DATADIR} or MLINKS get screwed up
MANPREFIX=	${PREFIX}/share/metaocaml

.if ${PORT_OPTIONS:MX11}
USE_XORG=	x11
CONFIGURE_ARGS+=-x11include ${LOCALBASE}/include -x11lib ${LOCALBASE}/lib
PLIST_SUB+=	X11=""
.else
PLIST_SUB+=	X11="@comment "
.endif

# We would like to use bsd.tcl.mk here, but we can't USE_TCL after including
# bsd.port.pre.mk and we can't test WITH_LABLTK before including bsd.port.pre.mk
.if ${PORT_OPTIONS:MLABLTK}
LIB_DEPENDS+=	tk84.1:${PORTSDIR}/x11-toolkits/tk84
CONFIGURE_ARGS+=-tkdefs "-I${LOCALBASE}/include/tcl8.4 -I${LOCALBASE}/include/tk8.4"
CONFIGURE_ARGS+=-tklibs "-L${LOCALBASE}/lib"
PLIST_SUB+=	LABLTK=""
.if ! ${PORT_OPTIONS:MX11}
CONFIGURE_ARGS+=-tk-no-x11
.endif
.else
CONFIGURE_ARGS+=-no-tk
PLIST_SUB+=	LABLTK="@comment "
.endif

post-patch:
	@${REINPLACE_CMD} -e \
		"s|-D_THREAD_SAFE|${PTHREAD_CFLAGS}|; \
		 s|-pthread|${PTHREAD_LIBS}|; \
		 s|aspp='gcc'|aspp='${CC}'|" ${WRKSRC}/configure
	@${FIND} ${WRKSRC} -type f -name Makefile -exec ${REINPLACE_CMD} -Ee \
		's,^([[:space:]]*(then)?[[:space:]]*)cp([[:space:]]+.*BINDIR),\1\$${BSD_INSTALL_PROGRAM} \3,; \
		 s,^([[:space:]]*(then)?[[:space:]]*)cp([[:space:]]+.*LIBDIR),\1\$${BSD_INSTALL_DATA} \3,; \
		 s,^([[:space:]]*(then)?[[:space:]]*)cp([[:space:]]+.*INSTALLDIR),\1\$${BSD_INSTALL_DATA} \3,; \
		 s,^([[:space:]]*(then)?[[:space:]]*)\$$\(CP\)([[:space:]]+.*BINDIR),\1\$${BSD_INSTALL_PROGRAM} \3,; \
		 s,^([[:space:]]*(then)?[[:space:]]*)\$$\(CP\)([[:space:]]+.*LIBDIR),\1\$${BSD_INSTALL_DATA} \3,; \
		 s,^([[:space:]]*(then)?[[:space:]]*)(\$$\(CP\)|cp)([[:space:]]+.*(MANDIR|MANODIR|MANEXT)),\1\$${BSD_INSTALL_MAN} \4,; \
		 s,([[:space:]]*then[[:space:]]*)cp([[:space:]]+.*LIBDIR),\1\$${BSD_INSTALL_DATA} \2,; \
		 s,([[:space:]]*then[[:space:]]*)cp([[:space:]]+.*BINDIR),\1\$${BSD_INSTALL_PROGRAM} \2,; \
		 s,([[:space:]]*(do|then)[[:space:]]*)(\$$\(CP\)|cp)([[:space:]]+.*(MANDIR|MANODIR|MANEXT)),\1\$${BSD_INSTALL_MAN} \4,; \
		 s,-O,,' {} \;

post-install:
.if ${PORT_OPTIONS:MLABLTK}
.  for d in camltk labltk
	${MKDIR} ${EXAMPLESDIR}/${d}
	${CP} -R ${WRKSRC}/otherlibs/labltk/examples_${d}/* ${EXAMPLESDIR}/${d}
.  endfor
	${CHOWN} -R ${SHAREOWN}:${SHAREGRP} ${EXAMPLESDIR}/*
	${FIND} ${EXAMPLESDIR}/* -type f -exec ${CHMOD} ${SHAREMODE} {} \;
	${FIND} ${EXAMPLESDIR}/* -type d -exec ${CHMOD} ${BINMODE} {} \;
.endif
	${LN} -sf ${PREFIX}/lib/metaocaml/bin/metaocaml ${PREFIX}/bin/metaocaml
	${LN} -sf ${PREFIX}/lib/metaocaml/bin/metaocamlopt ${PREFIX}/bin/metaocamlopt
	${LN} -sf ${PREFIX}/lib/metaocaml/bin/metaocamlc ${PREFIX}/bin/metaocamlc
.for p in camlp4o.opt camlp4r.opt ocamlc.opt ocamldep.opt ocamldoc.opt \
	ocamllex.opt ocamlopt.opt ocamlrun ocamlyacc
	${STRIP_CMD} ${PREFIX}/lib/metaocaml/bin/${p}
.endfor
	${CHMOD} u+w ${PREFIX}/lib/metaocaml/lib/ld.conf
.for dir in ${PLISTDIR}
	@${FIND} ${dir} ! -type d | \
		${SED} 's,^${PREFIX}/,,' >> ${TMPPLIST}
	@${FIND} ${dir} -type d | ${SORT} -r | \
		${SED} 's,^${PREFIX}/,@dirrm ,' >> ${TMPPLIST}
.endfor
	echo "@exec mkdir -p  %D/lib/metaocaml/lib/ocamldoc/custom" >> ${TMPPLIST}
	echo "@dirrm ${MANPREFIX:S|${PREFIX}/||}/man/man1" >> ${TMPPLIST}
	echo "@dirrm ${MANPREFIX:S|${PREFIX}/||}/man/mann" >> ${TMPPLIST}
	echo "@dirrm ${MANPREFIX:S|${PREFIX}/||}/man" >> ${TMPPLIST}
	echo "@dirrm ${MANPREFIX:S|${PREFIX}/||}" >> ${TMPPLIST}
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>

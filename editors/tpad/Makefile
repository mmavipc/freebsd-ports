# Created by: Antonio Bonifati <ant@monitor.deis.unical.it>
# $FreeBSD$

PORTNAME=	tpad
PORTVERSION=	1.3
PORTREVISION=	1
CATEGORIES=	editors tcl tk
MASTER_SITES=	SF/tclpad/tclpad/${PORTVERSION} \
		http://monitor.deis.unical.it/ant/tpad/ \
		http://queen.rett.polimi.it/~ant/tcl/script/ \
		http://sarovar.org/download.php/382/

MAINTAINER=	ant@monitor.deis.unical.it
COMMENT=	Windows XP (TM) enhanced Notepad clone written in Tcl/Tk

RUN_DEPENDS=	wish8.4:${PORTSDIR}/x11-toolkits/tk84

NO_BUILD=	yes

PORTDOCS=	ChangeLog bug.html conf.html embed.html index.html intro.html \
		keys.html log.html mouse.html tidy.html tidy.png todo tpad.html
MAN1=		tpad.1
MLINKS=		tpad.1 tview.1
PLIST_SUB=	LIBDIR=lib/tpad${PORTVERSION}
SUB_FILES=	pkg-message

NO_STAGE=	yes
do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/bin/tpad ${PREFIX}/bin/tpad
	@${MKDIR} ${PREFIX}/lib/tpad${PORTVERSION}/msgs
	cd ${WRKDIR}/lib/tpad${PORTVERSION}; \
	for libfile in *.tcl; do \
		${INSTALL_DATA} $$libfile ${PREFIX}/lib/tpad${PORTVERSION}; \
	done
	cd ${WRKDIR}/lib/tpad${PORTVERSION}/msgs; \
	for msgfile in *.msg; do \
		${INSTALL_DATA} $$msgfile ${PREFIX}/lib/tpad${PORTVERSION}/msgs; \
	done
	@${MKDIR} ${DATADIR}
	cd ${WRKDIR}/share/tpad/; \
	for  datafile in *; do \
		${INSTALL_DATA} $$datafile ${DATADIR}; \
	done

post-install:
	${TEST} -e ${PREFIX}/bin/tview || (cd ${PREFIX}/bin ; ${LN} -s tpad tview)
.if !defined(NO_INSTALL_MANPAGES)
	${INSTALL_MAN} ${WRKDIR}/man/man1/tpad.1 ${MANPREFIX}/man/man1
.endif
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
.for docfile in ${PORTDOCS}
	${INSTALL_DATA} ${WRKDIR}/share/doc/tpad/${docfile} ${DOCSDIR}
.endfor
.endif
	${INSTALL_DATA} ${WRKDIR}/etc/tpad.conf ${PREFIX}/etc/tpad.conf.sample
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>

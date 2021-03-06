# Created by: Mykola Khotyaintsev <ko@irfu.se>
# $FreeBSD$

PORTNAME=	vtk
PORTVERSION=	5.10.1
CATEGORIES=	math graphics
MASTER_SITES=	http://www.vtk.org/files/release/${PORTVERSION:R}/ \
		http://www.neuro.mcw.edu/Ports/distfiles/VTK5/

MAINTAINER=	gahr@FreeBSD.org
COMMENT=	The Visualization Toolkit

LIB_DEPENDS=	expat.[5-6]:${PORTSDIR}/textproc/expat2 \
		jpeg:${PORTSDIR}/graphics/jpeg \
		png15:${PORTSDIR}/graphics/png \
		tiff:${PORTSDIR}/graphics/tiff

LATEST_LINK=	vtk5

WRKSRC=		${WRKDIR}/VTK${PORTVERSION}

CONFLICTS=	vtk-4*

SUB_FILES=	vtk.3

USES=		cmake:outsource
USE_XORG=	xt
USE_LDCONFIG=	${PREFIX}/lib/vtk-${PORTVERSION:R}
CXXFLAGS+=	-DUSE_INTERP_ERRORLINE

OPTIONS_DEFINE=	SHARED VTKMPEG2 GL2PS OSMESA QT4 JAVA PYTHON TCLTK \
		DBGLEAKS LEGACY
OPTIONS_DEFAULT=SHARED GL2PS QT4 PYTHON TCLTK LEGACY

SHARED_DESC=	Build shared libraries
VTKMPEG2_DESC=	Patented MPEG2 encoder module
GL2PS_DESC=	OpenGL to PostScript conversion module
OSMESA_DESC=	Use Mesa for off-screen rendering
DBGLEAKS_DESC=	Build leak checking support
LEGACY_DESC=	Include legacy code

PLIST_SUB+=	VER1="${PORTVERSION}" \
		VER2="${PORTVERSION:R}" \
		VER3="${PORTVERSION:R:R}"

MAN3=		vtk.3
PORTDOCS=	README.html


CMAKE_ARGS+=	-DBUILD_DOCUMENTATION:BOOL=ON \
		-DBUILD_TESTING:BOOL=OFF \
		-DKWSYS_LFS_DISABLE:BOOL=ON \
		-DVTK_USE_PARALLEL:BOOL=ON \
		-DVTK_USE_GUISUPPORT:BOOL=ON \
		-DVTK_HAVE_GETSOCKNAME_WITH_SOCKLEN_T:BOOL=ON \
		-DVTK_DATA_ROOT:PATH=${EXAMPLESDIR}/VTKData \
		-DOPENGL_INCLUDE_DIR:PATH=${LOCALBASE}/include \
		-DOPENGL_gl_LIBRARY:FILEPATH=${LOCALBASE}/lib/libGL.so \
		-DOPENGL_glu_LIBRARY:FILEPATH=${LOCALBASE}/lib/libGLU.so

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MSHARED}
CMAKE_ARGS+=	-DBUILD_SHARED_LIBS:BOOL=ON \
		-DVTK_USE_SYSTEM_EXPAT:BOOL=ON \
		-DVTK_USE_SYSTEM_JPEG:BOOL=ON \
		-DVTK_USE_SYSTEM_PNG:BOOL=ON \
		-DVTK_USE_SYSTEM_TIFF:BOOL=ON \
		-DVTK_USE_SYSTEM_ZLIB:BOOL=ON
PLIST_SUB+=	SHARED="" \
		STATIC="@comment "
.else
CMAKE_ARGS+=	-DBUILD_SHARED_LIBS:BOOL=OFF \
		-DVTK_USE_SYSTEM_EXPAT:BOOL=OFF \
		-DVTK_USE_SYSTEM_JPEG:BOOL=OFF \
		-DVTK_USE_SYSTEM_PNG:BOOL=OFF \
		-DVTK_USE_SYSTEM_TIFF:BOOL=OFF \
		-DVTK_USE_SYSTEM_ZLIB:BOOL=OFF
PLIST_SUB+=	SHARED="@comment " \
		STATIC=""
.endif

.if ${PORT_OPTIONS:MVTKMPEG2}
LIB_DEPENDS+=	vtkMPEG2Encode:${PORTSDIR}/multimedia/vtkmpeg2encode
PLIST_SUB+=	MPEG=""
CMAKE_ARGS+=	-DVTK_USE_PATENTED:BOOL=ON \
		-DVTK_USE_MPEG2_ENCODER:BOOL=ON \
		-DvtkMPEG2Encode_INCLUDE_PATH=${LOCALBASE}/include/vtk-5.8 \
		-DvtkMPEG2Encode_LIBRARIES=${LOCALBASE}/lib/libvtkMPEG2Encode.so
.else
PLIST_SUB+=	MPEG="@comment "
.endif

.if ${PORT_OPTIONS:MGL2PS}
LIB_DEPENDS+=	gl2ps:${PORTSDIR}/print/gl2ps
CMAKE_ARGS+=	-DVTK_USE_GL2PS:BOOL=ON
PLIST_SUB+=	GL2PS=""
.else
PLIST_SUB+=	GL2PS="@comment "
.endif

.if ${PORT_OPTIONS:MOSMESA}
LIB_DEPENDS+=	OSMesa:${PORTSDIR}/graphics/libosmesa
CMAKE_ARGS+=	-DVTK_OPENGL_HAS_OSMESA:BOOL=ON \
		-DOSMESA_INCLUDE_DIR:PATH=${LOCALBASE}/include/Mesa \
		-DOSMESA_LIBRARY:FILEPATH=${LOCALBASE}/lib/libOSMesa.so \
		-DOPENGL_gl_LIBRARY:FILEPATH=${LOCALBASE}/lib/libOSMesa.so \
		-DVTK_USE_X:BOOL=OFF
PLIST_SUB+=	X11="@comment "
.else
USE_GL=		yes
CMAKE_ARGS+=	-DVTK_USE_X:BOOL=ON
PLIST_SUB+=	X11=""
.endif

.if ${PORT_OPTIONS:MQT4}
USE_QT4=	corelib designer gui opengl qmake_build uic_build \
		moc_build rcc_build
CMAKE_ARGS+=	-DVTK_USE_GUISUPPORT:BOOL=ON \
   		-DVTK_USE_QVTK:BOOL=ON \
   		-DVTK_USE_QT:BOOL=ON \
   		-DDESIRED_QT_VERSION:STRING=4 \
		-DQT_QMAKE_EXECUTABLE:FILEPATH=${QMAKE} \
		-DVTK_INSTALL_QT_DIR:FILEPATH=/lib/qt4/plugins/designer
PLIST_SUB+=	QT=""
.else
CMAKE_ARGS+=	-DVTK_USE_GUISUPPORT:BOOL=OFF
PLIST_SUB+=	QT="@comment "
.endif

.if ${PORT_OPTIONS:MPYTHON}
.if ${PORT_OPTIONS:MSHARED} == ""
IGNORE=		python wrapping requires shared libraries.\
		Run make config again and enable the SHARED option
.endif
USE_PYTHON=	yes
PYDISTUTILS_PKGNAME=	VTK
INSTALLS_EGGINFO=	yes
CMAKE_ARGS+=	-DVTK_WRAP_PYTHON:BOOL=ON \
   		-DVTK_PYTHON_SETUP_ARGS:STRING='--prefix="${PREFIX}"'
PLIST_SUB+=	PYTHON=""
.else
CMAKE_ARGS+=	-DVTK_WRAP_PYTHON:BOOL=OFF
PLIST_SUB+=	PYTHON="@comment "
.endif

.if ${PORT_OPTIONS:MTCLTK}
CMAKE_ARGS+=	-DVTK_WRAP_TCL:BOOL=ON
PLIST_SUB+=	TCLTK=""
.else
CMAKE_ARGS+=	-DVTK_WRAP_TCL:BOOL=OFF
PLIST_SUB+=	TCLTK="@comment "
.endif

# Used by both tcl/tk and python
.if ${PORT_OPTIONS:MTCLTK} || ${PORT_OPTIONS:MPYTHON}
USE_TCL=	84+
USE_TK=		84+
CMAKE_ARGS+=	-DVTK_USE_TK:BOOL=ON \
		-DTCL_INCLUDE_PATH=${TCL_INCLUDEDIR} \
		-DTK_INCLUDE_PATH=${TK_INCLUDEDIR}
PLIST_SUB+=	WRAP_PYTHON_OR_TCLTK="" \
		TCLTK_VER="${TCL_VER}"
.else
PLIST_SUB+=	WRAP_PYTHON_OR_TCLTK="@comment "
.endif

.if ${PORT_OPTIONS:MJAVA}
.if ${PORT_OPTIONS:MSHARED} == ""
IGNORE=		java wrapping requires shared libraries.\
		Run make config again and enable the SHARED option
.endif
.if ${ARCH} == "amd64"
CXXFLAGS+=	-fPIC
.endif
CATEGORIES+=	java
USE_JAVA=	yes
JAVA_VENDOR=	openjdk
JAVA_VERSION=	1.6+
CMAKE_ARGS+=	-DVTK_WRAP_JAVA:BOOL=ON \
    		-DJAVA_AWT_INCLUDE_PATH:FILEPATH=${JAVA_HOME}/include \
    		-DJAVA_INCLUDE_PATH:FILEPATH=${JAVA_HOME}/include \
    		-DJAVA_INCLUDE_PATH2:FILEPATH=${JAVA_HOME}/include/freebsd \
		-DJAVA_AWT_LIBRARY:FILEPATH=${JAVA_HOME}/jre/lib/${ARCH}/libjawt.so \
		-DJAVA_JVM_LIBRARY:FILEPATH=${JAVA_HOME}/jre/lib/${ARCH}/server/libjvm.so
PLIST_SUB+=	JAVA=""
.else
PLIST_SUB+=	JAVA="@comment "
.endif

# Wrapping
.if ${PORT_OPTIONS:MPYTHON} || ${PORT_OPTIONS:MTCLTK} || ${PORT_OPTIONS:MJAVA}
PLIST_SUB+=	WRAPPING=""
.else
PLIST_SUB+=	WRAPPING="@comment "
.endif

.if ${PORT_OPTIONS:MDBGLEAKS}
CMAKE_ARGS+=	-DVTK_DEBUG_LEAKS:BOOL=ON
.else
CMAKE_ARGS+=	-DVTK_DEBUG_LEAKS:BOOL=OFF
.endif

.if ${PORT_OPTIONS:MLEGACY}
CMAKE_ARGS+=	-DVTK_LEGACY_REMOVE:BOOL=OFF
PLIST_SUB+=	LEGACY=""
.else
CMAKE_ARGS+=	-DVTK_LEGACY_REMOVE:BOOL=ON
PLIST_SUB+=	LEGACY="@comment "
.endif

post-patch:
	${REINPLACE_CMD} -e 's|malloc.h|stdlib.h|g' \
	    ${WRKSRC}/Hybrid/vtkVRMLImporter.cxx
#	${REINPLACE_CMD} -e '222s|)|) \&\& !defined(__FreeBSD__)|' \
#	    ${WRKSRC}/Utilities/kwsys/SharedForward.h.in
	${REINPLACE_CMD} -e '25,30d' ${WRKSRC}/Wrapping/Python/setup.py.in
.if ${PORT_OPTIONS:MSHARED}
	${REINPLACE_CMD} -e 's|png_set_gray_1_2_4_to_8|png_set_expand_gray_1_2_4_to_8|g' \
	    ${WRKSRC}/IO/vtkPNGReader.cxx
.endif

post-configure:
.if ${PORT_OPTIONS:MJAVA}
	${REINPLACE_CMD} -e 's|-ljawt$$||' \
	    ${CONFIGURE_WRKSRC}/Wrapping/Java/CMakeFiles/VTKJavaExecutable.dir/link.txt
.endif

pre-install:
.if ${PORT_OPTIONS:MPYTHON}
	${MKDIR} ${PYTHONPREFIX_SITELIBDIR}
.endif
	${MKDIR} ${MANPREFIX}/man/man3
	${INSTALL_MAN} ${WRKDIR}/vtk.3 ${MANPREFIX}/man/man3
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README.html ${DOCSDIR}
.endif

LIBS_TOFIX=	vtkNetCDF_cxx vtkhdf5
LIBDIR=		${PREFIX}/lib/vtk-${PORTVERSION:R}/

post-install:
# Ports system wants us to conform to lib.so.x format, but VTK5
# only installs lib.so.x.y and lib.so.x.y.z.
.if ${PORT_OPTIONS:MSHARED}
	@for lib in ${LIBS_TOFIX}; do \
		${CP} ${LIBDIR}/lib$$lib.so ${LIBDIR}/lib$$lib.so.${PORTVERSION}; \
	done
	@for lib in ${LIBDIR}/*.so; do \
	    ${RM} -f $$lib; \
		 ${LN} -sf $$lib.${PORTVERSION} $$lib.${PORTVERSION:R}; \
		 ${LN} -sf $$lib.${PORTVERSION:R} $$lib.${PORTVERSION:R:R}; \
		 ${LN} -sf $$lib.${PORTVERSION:R:R} $$lib; \
	done
.if ${PORT_OPTIONS:MQT4}
	@for lib in ${LIBDIR}/libQVTK*.so; do \
	    ${RM} -f $$lib; \
	    ${LN} -sf $$lib.${PORTVERSION} $$lib; \
	    ${LN} -sf $$lib.${PORTVERSION} $$lib.${PORTVERSION:R:R}; \
	done
.endif
.endif
.if ${PORT_OPTIONS:MVTKMPEG2}
	@${ECHO_CMD}
	@${ECHO_CMD} "This port uses the patented MPEG2 encoder."
	@${ECHO_CMD}
.endif

.include <bsd.port.mk>

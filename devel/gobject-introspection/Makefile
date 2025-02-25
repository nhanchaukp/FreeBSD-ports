# Created by: Alexander Logvinov <avl@FreeBSD.org>

PORTNAME=	gobject-introspection
DISTVERSION=	1.70.0
PORTEPOCH=	1
CATEGORIES=	devel
MASTER_SITES=	GNOME
DIST_SUBDIR=	gnome

PATCH_SITES=	https://gitlab.gnome.org/GNOME/${PORTNAME}/-/commit/
PATCHFILES+=	effb1e09dee2.patch:-p1 # https://gitlab.gnome.org/GNOME/gobject-introspection/-/merge_requests/305

MAINTAINER=	desktop@FreeBSD.org
COMMENT=	Generate interface introspection data for GObject libraries

LICENSE=	GPLv2+ LGPL20+
LICENSE_COMB=	multi
LICENSE_FILE_LGPL20+ =	${WRKSRC}/COPYING.LGPL
LICENSE_FILE_GPLv2+ =	${WRKSRC}/COPYING.GPL

# we need cairo otherwise the generated Cairo gir is broken
BUILD_DEPENDS=	cairo-trace:graphics/cairo
LIB_DEPENDS=	libffi.so:devel/libffi

PORTSCOUT=	limitw:1,even

USES=		bison gettext gnome localbase meson pkgconfig python:3.6+ tar:xz
USE_GNOME=	glib20
USE_LDCONFIG=	yes
MESON_ARGS=	-Ddoctool=disabled \
		-Dpython=${PYTHON_CMD}

post-patch:
	@${REINPLACE_CMD} -e 's|%%PYTHON_CMD%%|${PYTHON_CMD}|' ${WRKSRC}/tools/meson.build

post-stage:
	@${PYTHON_CMD} -m compileall -d ${PREFIX}/lib/${PORTNAME} \
		"${STAGEDIR}${PREFIX}/lib/${PORTNAME}"
	@${PYTHON_CMD} -O -m compileall -d ${PREFIX}/lib/${PORTNAME} \
		"${STAGEDIR}${PREFIX}/lib/${PORTNAME}"

post-install:
	@${RM} ${STAGEDIR}${PREFIX}/lib/gobject-introspection/giscanner/doctemplates/*/meson.build*

.include <bsd.port.mk>

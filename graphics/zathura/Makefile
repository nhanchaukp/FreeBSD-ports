# Created by: Quentin Stievenart <acieroid@awesom.eu>

PORTNAME=	zathura
DISTVERSION=	0.4.5
CATEGORIES=	graphics print
MASTER_SITES=	https://git.pwmt.org/pwmt/${PORTNAME}/-/archive/${DISTVERSION}/

PATCH_SITES=	https://git.pwmt.org/pwmt/${PORTNAME}/-/commit/
PATCHFILES+=	c6ec5044c5ff.patch:-p1 # meson 0.61

MAINTAINER=	quentin.stievenart@gmail.com
COMMENT=	Customizable lightweight pdf viewer

LICENSE=	ZLIB
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libcairo.so:graphics/cairo \
		libgirara-gtk3.so:x11-toolkits/girara \
		libsynctex.so:devel/tex-synctex
BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}sphinx>=1.2.2,1:textproc/py-sphinx@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}sphinx_rtd_theme>0:textproc/py-sphinx_rtd_theme@${PY_FLAVOR}

USES=		compiler:c11 gettext-tools:build gnome meson ninja pkgconfig \
		python:3.6+
USE_GNOME=	glib20 gtk30 gdkpixbuf2

OPTIONS_DEFINE=		SQLITE
OPTIONS_DEFAULT=	SQLITE

SQLITE_USES=		sqlite
SQLITE_MESON_ENABLED=	sqlite

.include <bsd.port.mk>

PORTNAME=	qutebrowser
DISTVERSION=	2.4.0
PORTREVISION=	1
CATEGORIES=	www
MASTER_SITES=	CHEESESHOP

MAINTAINER=	novel@FreeBSD.org
COMMENT=	Keyboard-focused browser with a minimal GUI

LICENSE=	GPLv3

RUN_DEPENDS=	\
		${PYTHON_PKGNAMEPREFIX}colorama>=0:devel/py-colorama@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}Jinja2>=0:devel/py-Jinja2@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}markupsafe>=0:textproc/py-markupsafe@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}pygments>=0:textproc/py-pygments@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}yaml>0:devel/py-yaml@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}sip>=0:devel/py-sip@${PY_FLAVOR} \
		${LOCALBASE}/lib/alsa-lib/libasound_module_pcm_oss.so:audio/alsa-plugins

USES=		cpe desktop-file-utils python:3.6+ pyqt:5 qt:5
USE_PYQT=	pyqt5
USE_PYTHON=	distutils autoplist noflavors
USE_QT=		sql-sqlite3

# Upstream archive contains files with UTF-8 names
EXTRACT_CMD=	${SETENV} LC_ALL=en_US.UTF-8 /usr/bin/bsdtar
NO_ARCH=	yes
PLIST_FILES=	share/applications/${PORTNAME}-${PYTHON_VER}.desktop

OPTIONS_DEFINE=		WEBENGINE
OPTIONS_DEFINE_amd64=	ADBLOCK
OPTIONS_DEFAULT_amd64=	WEBENGINE ADBLOCK
OPTIONS_DEFAULT_i386=	WEBENGINE

ADBLOCK_DESC=		Enable the newer adblocking support
WEBENGINE_DESC=		WebEngine webpage renderer support

ADBLOCK_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}adblock>=0.4.2:www/py-adblock@${PY_FLAVOR}
WEBENGINE_USE=	PYQT=webengine

.include <bsd.port.pre.mk>

.if ${PYTHON_REL} < 30900
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}importlib-resources>0:devel/py-importlib-resources@${PY_FLAVOR}
.endif

post-install:
	${INSTALL_DATA} ${WRKSRC}/misc/org.qutebrowser.qutebrowser.desktop \
		${STAGEDIR}${PREFIX}/share/applications/${PORTNAME}-${PYTHON_VER}.desktop

.include <bsd.port.post.mk>

# Created by: Kubilay Kocak <koobs@FreeBSD.org>

PORTNAME=	bleach
PORTVERSION=	3.1.5
CATEGORIES=	www python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Easy safelist-based HTML-sanitizing tool

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}six>=1.9.0:devel/py-six@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}webencodings>0:converters/py-webencodings@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}packaging>0:devel/py-packaging@${PY_FLAVOR}
TEST_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pytest>=3.0.0:devel/py-pytest@${PY_FLAVOR}

USES=		cpe python:3.6+
USE_PYTHON=	autoplist distutils

CPE_VENDOR=	mozilla

NO_ARCH=	yes

# This is a development script
# TODO: Remove from sdist (via MANIFEST.ini)
post-extract:
	${RM} ${WRKSRC}/bleach/_vendor/pip_install_vendor.sh

do-test:
	@cd ${WRKSRC} && ${PYTHON_CMD} -m pytest -v -rs -o addopts=

.include <bsd.port.mk>

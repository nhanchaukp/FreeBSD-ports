# Created by: Piotr Kubaj <pkubaj@anongoth.pl>

PORTNAME=	flac
PORTVERSION=	1.3.0
DISTVERSIONSUFFIX=	-5.el7_1
PORTREVISION=	2
CATEGORIES=	audio linux
PKGNAMESUFFIX=	-libs
DISTFILES_aarch64=	flac-libs-1.3.0-5.el7.centos${EXTRACT_SUFX_aarch64}:aarch64

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	Free lossless audio codec (Linux CentOS ${LINUX_DIST_VER})

USES=		cpe linux:c7
USE_LDCONFIG=	yes
USE_LINUX=	libogg
USE_LINUX_RPM=	yes

CPE_VENDOR=	flac_project

LIB_DISTNAMES=	${PORTNAME}${PKGNAMESUFFIX}-${DISTVERSIONFULL}

CONFLICTS=	linux-c6-${PORTNAME}
DESCR=		${.CURDIR}/../${PORTNAME}/pkg-descr
DOCSDIR=	${PREFIX}/usr/share/doc/${PORTNAME}${PKGNAMESUFFIX}-${PORTVERSION}

OPTIONS_DEFINE=	DOCS

.include <bsd.port.mk>

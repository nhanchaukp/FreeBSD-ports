PORTNAME=	tarantool-c
PORTVERSION=	1.0.1
PORTREVISION=	5
CATEGORIES=	databases

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	C client for Tarantool 1.6+

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libmsgpuck.so:devel/msgpuck

USES=		cmake compiler:c11

CMAKE_OFF=	ENABLE_BUNDLED_DOCS ENABLE_BUNDLED_MSGPUCK

USE_GITHUB=	yes
GH_ACCOUNT=	tarantool
GH_TAGNAME=	2aa7937

.include <bsd.port.mk>

PORTNAME=	ergo
DISTVERSIONPREFIX=	v
DISTVERSION=	2.9.1
CATEGORIES=	irc
PKGNAMESUFFIX=	-irc-server

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	Modern IRC server (daemon/ircd) written in Go

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go:modules
USE_GITHUB=	yes
GH_ACCOUNT=	ergochat

CONFLICTS_INSTALL=	ergo

GO_PKGNAME=	github.com/${GH_ACCOUNT}/${PORTNAME}

PLIST_FILES=	bin/${PORTNAME}

.include <bsd.port.mk>

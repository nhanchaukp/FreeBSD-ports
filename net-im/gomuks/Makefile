# Created by: Emanuel Haupt <ehaupt@FreeBSD.org>

PORTNAME=	gomuks
PORTVERSION=	0.2.4
DISTVERSIONPREFIX=	v
CATEGORIES=	net-im

MAINTAINER=	ehaupt@FreeBSD.org
COMMENT=	Terminal Matrix client written in Go

LICENSE=	AGPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libolm.so:security/olm

USES=		go:modules

GO_MODULE=	github.com/tulir/gomuks

PLIST_FILES=	bin/gomuks

.include <bsd.port.mk>

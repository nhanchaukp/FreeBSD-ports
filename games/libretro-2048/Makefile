PORTNAME=	libretro-2048
PORTVERSION=	0.20210214
CATEGORIES=	games

MAINTAINER=	dmenelkir@gmail.com
COMMENT=	Port of 2048 puzzle game to the libretro API

LICENSE=	GPLv2

USES=		compiler:c++11-lib gmake
USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	libretro
GH_TAGNAME=	35a299c

PLIST_FILES=	lib/libretro/2048_libretro.so

MAKEFILE=	Makefile.libretro

do-install:
	${MKDIR} ${STAGEDIR}/${PREFIX}/lib/libretro;
	${INSTALL_LIB} ${WRKSRC}/2048_libretro.so ${STAGEDIR}/${PREFIX}/lib/libretro;

.include <bsd.port.mk>

# Created by: Gea-Suan Lin <gslin@gslin.org>

PORTNAME=	schroedinger
PORTVERSION=	1.0.11
PORTREVISION=	4
CATEGORIES=	multimedia
MASTER_SITES=	http://diracvideo.org/download/schroedinger/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	High-speed Dirac codec

LICENSE=	GPLv2 LGPL20 MIT MPL11
LICENSE_COMB=	dual
LICENSE_FILE_MIT=	${WRKSRC}/COPYING.MIT
LICENSE_FILE_MPL11=	${WRKSRC}/COPYING.MPL

BROKEN=		Unfetchable
DEPRECATED=	Abandoned legacy video codec, upstream is dead and last release was back in 2012.
EXPIRATION_DATE=2022-03-31

LIB_DEPENDS=	liborc-0.4.so:devel/orc

USES=		libtool pkgconfig
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_LDCONFIG=	yes

post-patch:
	@${REINPLACE_CMD} -e 's|^pkgconfigdir=.*|pkgconfigdir="\\$${prefix}/libdata/pkgconfig"|' \
		${WRKSRC}/configure
# Derived from upstream git commit ee011f33f80c9691a6cfd5116101fdcf8c3cd6f7
	@${REINPLACE_CMD} '/^wavelet_max_gain_OBJECTS =/s/=/= tmp-orc.$$(OBJEXT)/' \
		${WRKSRC}/testsuite/Makefile.in

.include <bsd.port.mk>

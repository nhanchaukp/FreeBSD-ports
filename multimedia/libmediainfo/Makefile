# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	libmediainfo
PORTVERSION=	21.09
PORTREVISION=	1
CATEGORIES=	multimedia
MASTER_SITES=	https://mediaarea.net/download/binary/mediainfo/${PORTVERSION}/ \
		LOCAL/sunpoet
DISTNAME=	MediaInfo_CLI_${PORTVERSION}_GNU_FromSource

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	MediaInfo library

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/../../../License.html

LIB_DEPENDS=	libzen.so:multimedia/libzen

CONFLICTS_INSTALL=	mediainfo-0.[0-6]* mediainfo-0.7.[0-5]*

OPTIONS_DEFINE=	CURL MMS TINYXML2
OPTIONS_DEFAULT=TINYXML2
TINYXML2_DESC=	Use textproc/tinyxml2 instead of bundled one

USES=		alias compiler:c++11-lang libtool localbase pathfix pkgconfig tar:xz

CFLAGS+=	-D_POSIX_PRIORITY_SCHEDULING
CONFIGURE_ARGS=	--enable-shared --enable-static
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_CXXSTD=	c++11
USE_LDCONFIG=	yes

WRKSRC=		${WRKDIR}/MediaInfo_CLI_GNU_FromSource/MediaInfoLib/Project/GNU/Library

CURL_CONFIGURE_ON=	--with-libcurl=${LOCALBASE}
CURL_LIB_DEPENDS=	libcurl.so:ftp/curl
MMS_CONFIGURE_ON=	--with-libmms=${LOCALBASE}
MMS_LIB_DEPENDS=	libmms.so:net/libmms
TINYXML2_CONFIGURE_ON=	--with-libtinyxml2=yes
TINYXML2_LIB_DEPENDS=	libtinyxml2.so:textproc/tinyxml2

post-install:
	${INSTALL_DATA} ${WRKSRC}/libmediainfo.pc ${STAGEDIR}${PREFIX}/libdata/pkgconfig/libmediainfo.pc
	${RM} -r ${STAGEDIR}${PREFIX}/include/MediaInfoDLL/

.include <bsd.port.mk>

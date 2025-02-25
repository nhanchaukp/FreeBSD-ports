PORTNAME=	gerbera
DISTVERSIONPREFIX=	v
DISTVERSION=	1.10.0
CATEGORIES=	net multimedia

PATCH_SITES=	https://github.com/${PORTNAME}/${PORTNAME}/commit/
PATCHFILES=	97c5a5fbc27452ee5970f9c7be946d3819a79d05.patch:-p1

MAINTAINER=	diizzy@FreeBSD.org
COMMENT=	Media server compatible with DLNA and UPnP

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/LICENSE.md

LIB_DEPENDS=	libfmt.so:devel/libfmt \
		libspdlog.so:devel/spdlog \
		libpugixml.so:textproc/pugixml \
		libinotify.so:devel/libinotify

USES=		cmake compiler:c++17-lang iconv localbase:ldflags \
		pkgconfig sqlite

USE_GITHUB=	yes
USE_RC_SUBR=	gerbera

CMAKE_OFF=	WITH_EXIF WITH_LASTFM WITH_MYSQL WITH_SYSTEMD

SUB_FILES=	pkg-message
SUB_LIST=	USER=${USERS} GROUP=${GROUPS}

USERS=		gerbera
GROUPS=		gerbera

PLIST_SUB=	USER=${USERS} GROUP=${GROUPS}

OPTIONS_DEFINE=		CURL DEBUG DUKTAPE EXIV2 FFMPEG FFMPEGTHUMBNAILER \
			LIBMAGIC MATROSKA TAGLIB TEST
OPTIONS_DEFAULT=	CURL DUKTAPE EXIV2 FFMPEG LIBMAGIC TAGLIB LIBNPUPNP

OPTIONS_SINGLE=		UPNPLIB
OPTIONS_SINGLE_UPNPLIB=	LIBNPUPNP LIBUPNP

CURL_DESC=		Support for online services via cURL
DUKTAPE_DESC=		Javascript support for custom import scripts
FFMPEGTHUMBNAILER_DESC=	Support for thumbnail generation
LIBMAGIC_DESC=		Identify file mime types via libmagic
LIBNPUPNP_DESC=		Use high performance libnpupnp library
LIBUPNP_DESC=		Use libupnp library
MATROSKA_DESC=		Extract video/mkv metadata via libmatroska
TAGLIB_DESC=		Extract audio file metadata via taglib

CURL_LIB_DEPENDS=	libcurl.so:ftp/curl
CURL_CMAKE_BOOL=	WITH_CURL

DEBUG_CMAKE_BOOL=	WITH_DEBUG

DUKTAPE_LIB_DEPENDS=	libduktape.so:lang/duktape-lib
DUKTAPE_CMAKE_BOOL=	WITH_JS

EXIV2_LIB_DEPENDS=	libexiv2.so:graphics/exiv2
EXIV2_CMAKE_BOOL=	WITH_EXIV2

FFMPEGTHUMBNAILER_IMPLIES=	FFMPEG
FFMPEGTHUMBNAILER_LIB_DEPENDS=	libffmpegthumbnailer.so:multimedia/ffmpegthumbnailer
FFMPEGTHUMBNAILER_CMAKE_BOOL=	WITH_FFMPEGTHUMBNAILER

FFMPEG_LIB_DEPENDS=	libavformat.so:multimedia/ffmpeg \
			libavutil.so:multimedia/ffmpeg
FFMPEG_CMAKE_BOOL=	WITH_AVCODEC

LIBMAGIC_LIB_DEPENDS=	libmagic.so:sysutils/file
LIBMAGIC_CMAKE_BOOL=	WITH_MAGIC

LIBNPUPNP_LIB_DEPENDS=	libnpupnp.so:net/libnpupnp
LIBNPUPNP_CMAKE_BOOL=	WITH_NPUPNP

LIBUPNP_LIB_DEPENDS=	libupnp.so:devel/upnp

MATROSKA_LIB_DEPENDS=	libmatroska.so:multimedia/libmatroska
MATROSKA_CMAKE_BOOL=	WITH_MATROSKA

TAGLIB_LIB_DEPENDS=	libtag.so:audio/taglib
TAGLIB_CMAKE_BOOL=	WITH_TAGLIB

TEST_IMPLIES=		CURL DUKTAPE
TEST_BUILD_DEPENDS=	googletest>=0:devel/googletest
TEST_CMAKE_BOOL=	WITH_TESTS
TEST_TEST_TARGET=	test

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/gerbera
	@${MKDIR} ${STAGEDIR}/var/db/gerbera
	@${MKDIR} ${STAGEDIR}/var/log/gerbera
	@${STAGEDIR}${PREFIX}/bin/gerbera -f /var/db/gerbera --create-config > ${STAGEDIR}${PREFIX}/etc/gerbera-config.xml.sample

.include <bsd.port.mk>

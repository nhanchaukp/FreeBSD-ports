# Created by: Emanuel Haupt <ehaupt@critical.ch>

PORTNAME=	festalon
PORTVERSION=	0.5.5
PORTREVISION=	14
CATEGORIES=	audio
MASTER_SITES=	http://projects.raphnet.net/festalon/ \
		LOCAL/ehaupt

MAINTAINER=	ehaupt@FreeBSD.org
COMMENT=	Command line player for .nsf and .hes audio files

LICENSE=	GPLv2+
LICENSE_FILE=	${WRKSRC}/COPYING

ONLY_FOR_ARCHS=	amd64 powerpc powerpc64 powerpc64le

LIB_DEPENDS=	libsamplerate.so:audio/libsamplerate

USES=		cpe libtool pkgconfig sdl tar:bzip2
USE_SDL=	sdl

GNU_CONFIGURE=	yes

WRKSRC=		${WRKDIR}/${PORTNAME}

OPTIONS_DEFINE=	DOCS

PLIST_FILES=	bin/festalon
PORTDOCS=	README

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/src/${PORTNAME} \
		${STAGEDIR}${PREFIX}/bin/${PORTNAME}

do-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>

# Created by: Ying-Chieh Liao <ijliao@FreeBSD.org>

PORTNAME=	itext
PORTVERSION=	4.2.0
PORTREVISION=	5
PORTEPOCH=	1
CATEGORIES=	devel java
MASTER_SITES=	LOCAL/ale

MAINTAINER=	ale@FreeBSD.org
COMMENT=	Java-PDF Library

LICENSE=	LGPL20+ MPL11
LICENSE_COMB=	dual

DEPRECATED=	Outdated version and deprecated by upstream
EXPIRATION_DATE=2022-03-31

BUILD_DEPENDS=	${JAVALIBDIR}/bcmail.jar:java/bouncycastle \
		${JAVALIBDIR}/dom4j.jar:textproc/dom4j \
		${JAVALIBDIR}/pdf-renderer.jar:print/pdf-renderer
RUN_DEPENDS=	${JAVALIBDIR}/bcmail.jar:java/bouncycastle \
		${JAVALIBDIR}/dom4j.jar:textproc/dom4j \
		${JAVALIBDIR}/pdf-renderer.jar:print/pdf-renderer

OPTIONS_DEFINE=	DOCS

USES=		cpe dos2unix tar:bzip2
CPE_VENDOR=	${PORTNAME}pdf
DOS2UNIX_GLOB=	*.java
USE_JAVA=	yes
USE_ANT=	yes
ALL_TARGET=	jar jar.rtf jar.rups
MAKE_ENV=	ANT_INCLUDE_SHARED_JARS=YES
NO_ARCH=	yes

PLIST_FILES=	%%JAVAJARDIR%%/${PORTNAME}.jar \
		%%JAVAJARDIR%%/${PORTNAME}-rtf.jar \
		%%JAVAJARDIR%%/${PORTNAME}-rups.jar \
		bin/${PORTNAME}-rups

PORTDOCS=	*

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MDOCS}
ALL_TARGET+=	javadoc
.endif

do-install:
	${INSTALL_DATA} ${WRKDIR}/lib/iText.jar \
		${STAGEDIR}${JAVAJARDIR}/${PORTNAME}.jar
	${INSTALL_DATA} ${WRKDIR}/lib/iText-rtf.jar \
		${STAGEDIR}${JAVAJARDIR}/${PORTNAME}-rtf.jar
	${INSTALL_DATA} ${WRKDIR}/lib/iText-rups.jar \
		${STAGEDIR}${JAVAJARDIR}/${PORTNAME}-rups.jar
	${INSTALL_SCRIPT} ${FILESDIR}/${PORTNAME}-rups \
		${STAGEDIR}${PREFIX}/bin/
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}/apidocs
	(cd ${WRKDIR}/build/docs && ${COPYTREE_SHARE} . ${STAGEDIR}${DOCSDIR}/apidocs)
.endif

.include <bsd.port.mk>

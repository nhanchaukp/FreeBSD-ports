# Created by: Stefan Ehmann <shoesoft@gmx.net>

PORTNAME=		Ice
PORTVERSION=		3.6.5
DISTVERSIONPREFIX=	v
CATEGORIES=		devel

MAINTAINER=		grembo@FreeBSD.org
COMMENT=		Modern alternative to object middleware such as CORBA/COM/DCOM/COM+

LICENSE=		GPLv2

SLAVE_PORT?=		no
CONFLICTS=		Ice37 py*-Ice37 php*-Ice37

MAKE_JOBS_UNSAFE=	yes

.if ${SLAVE_PORT} == "no"
LIB_DEPENDS=		libexpat.so:textproc/expat2 \
			libmcpp.so:devel/mcpp
USES+=			compiler:c++11-lang ssl
.else
LIB_VRS=		${PORTVERSION:R:S|.||g}
LIB_DEPENDS+=		libIce.so.${LIB_VRS}:devel/ice
PLIST_SUB+=		LIB_VERSION="${PORTVERSION}" LIB_VRS="${LIB_VRS}"
.endif

OPTIONS_DEFINE?=	DEBUG TEST

USES+=			bdb:5 iconv gmake
INVALID_BDB_VER=	48 6
USE_LDCONFIG=		yes
BUILD_WRKSRC?=		${WRKSRC}/cpp
INSTALL_WRKSRC?=	${WRKSRC}/cpp
PORTSCOUT=		limit:^3\.6\.
USE_GITHUB=		yes
GH_TUPLE=		zeroc-ice:ice:${DISTVERSIONFULL}
TEST_GH_TUPLE=		zeroc-ice:ice:v3.7.6:CERTS

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MTEST} && ${SLAVE_PORT} == "no"
USES+=			python:build
BUILD_DEPENDS+=		${PYTHON_PKGNAMEPREFIX}passlib>0:security/py-passlib@${PY_FLAVOR}
.endif

CFLAGS+=		-ftemplate-depth-128 -fPIC -DPIC -Wall -D_REENTRANT -I${LOCALBASE}/include

.if !${PORT_OPTIONS:MDEBUG}
CFLAGS+=		-DNDEBUG
.endif

# determine if we are on a 64-bit arch
.if ${ARCH:M*64*}
MAKE_ENV+=		LP64=yes
.endif

.if !${PORT_OPTIONS:MTEST}
MAKE_ENV+=		NOTESTS=yes
.endif

.if ${SLAVE_PORT} == "no"
MAKE_ENV+=		LD_LIBRARY_PATH=${WRKSRC}/cpp/lib:$$LD_LIBRARY_PATH
.endif

.include <bsd.port.pre.mk>

.if ${PREFIX} != ${LOCALBASE}
PYSITEDIR=	${PREFIX}${PYTHON_SITELIBDIR:S|^${LOCALBASE}||}
.else
PYSITEDIR=	${PYTHON_SITELIBDIR}
.endif

post-patch:
	@${SED} 's|%%PREFIX%%|${STAGEDIR}${PREFIX}|g; \
		s|%%DATADIR%%|${STAGEDIR}${DATADIR}|g; \
		s|%%DOCSDIR%%|${STAGEDIR}${DOCSDIR}|g; \
		s|%%ICONV_LIB%%|${ICONV_LIB}|g; \
		s|%%INSTALL_PROGRAM%%|${INSTALL_PROGRAM}|g; \
		s|%%INSTALL_DATA%%|${INSTALL_DATA}|g; \
		s|%%OPENSSLLIB%%|${OPENSSLLIB}|g; \
		s|%%OPENSSLINC%%|${OPENSSLINC}|g; \
		s|%%OPENSSLRPATH%%|${OPENSSLRPATH}|g;' \
		${FILESDIR}/Make.rules.FreeBSD > ${WRKSRC}/cpp/config/Make.rules.FreeBSD
	@${REINPLACE_CMD} 's|%%BDB_LIB_CXX_NAME%%|${BDB_LIB_CXX_NAME}|g; \
		s|%%BDB_LIB_DIR%%|${BDB_LIB_DIR}|g; \
		s|%%BDB_INCLUDE_DIR%%|${BDB_INCLUDE_DIR}|g; \
		s|%%OPENSSLLIB%%|${OPENSSLLIB}|g; \
		s|%%OPENSSLINC%%|${OPENSSLINC}|g; \
		s|%%OPENSSLRPATH%%|${OPENSSLRPATH}|g; \
		/install_docdir/d' \
		${WRKSRC}/cpp/config/Make.rules
	@${REINPLACE_CMD} 's|%%OPENSSLBASE%%|${OPENSSLBASE}|g;' \
		${WRKSRC}/cpp/test/IceSSL/configuration/run.py
	@${REINPLACE_CMD} '/install_configdir/d' \
		${WRKSRC}/cpp/config/Make.rules
	@${REINPLACE_CMD} '/LICENSE/s/prefix/install_slicedir/; \
		s|%%INSTALL_PROGRAM%%|${INSTALL_PROGRAM}|g;' \
		${WRKSRC}/config/Make.common.rules
	@${REINPLACE_CMD} 's|%%INSTALL_PROGRAM%%|${INSTALL_PROGRAM}|g; \
		s|%%INSTALL_DATA%%|${INSTALL_DATA}|g; \
		s|%%ICONV_LIB%%|${ICONV_LIB}|g; \
		s|%%PYTHON_CMD%%|${PYTHON_CMD}|g; \
		s|%%PYTHON_SITELIBDIR%%|${STAGEDIR}${PYSITEDIR}|g; \
		s|%%PREFIX%%|${PREFIX}|g; \
		s|%%LOCALBASE%%|${LOCALBASE}|g' ${WRKSRC}/python/config/Make.rules
	@${REINPLACE_CMD} 's|%%INSTALL_PROGRAM%%|${INSTALL_PROGRAM}|g; \
		s|%%INSTALL_DATA%%|${INSTALL_DATA}|g; \
		s|%%PREFIX%%|${PREFIX}|g; \
		s|%%LOCALBASE%%|${LOCALBASE}|g;' ${WRKSRC}/php/config/Make.rules.php

do-test-TEST-on:
	@${RM} -r ${WRKSRC}/certs
	@${CP} -r ${WRKSRC_CERTS}/certs ${WRKSRC}/certs
	@cd ${BUILD_WRKSRC} && ${PYTHON_CMD} ./allTests.py

.if ${SLAVE_PORT} == "no"
post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/*.so.*
.endif

.include <bsd.port.post.mk>

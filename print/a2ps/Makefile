# Created by: Chuck Robey <chuckr@FreeBSD.org>

PORTNAME=	a2ps
PORTVERSION=	4.13b
PORTREVISION=	16
CATEGORIES=	print
MASTER_SITES=	GNU LOCAL/hrs/a2ps/:i18n

MAINTAINER=	dinoex@FreeBSD.org
COMMENT=	Formats an ASCII file for printing on a postscript printer

LICENSE=	GPLv2

LIB_DEPENDS=	libpaper.so:print/libpaper

PORTSCOUT=	skipv:4.14

USES=		perl5 cpe
USE_CSTD=	gnu89
GNU_CONFIGURE=	yes
USE_LDCONFIG=	yes
INFO=		a2ps ogonkify regex
WRKSRC=		${WRKDIR}/${PORTNAME}-4.13
I18N_PACKAGE=	i18n-fonts-0.1
CPE_VENDOR=	gnu
# CVE-2015-8107 fixed in files/patch-output.c
# CVE-2014-0466 fixed in files/patch-fixps.in
# CVE-2004-1377 fixed in files/patch-fixps.in files/patch-contrib-tmpdircreation
# CVE-2004-1170 fixed in files/patch-select.c
# CVE-2001-1593 fixed in files/patch-routines.[hc]

CONFIGURE_ARGS=	--with-medium=libpaper --sharedstatedir=${PREFIX}/share \
	--sysconfdir=${PREFIX}/etc --datadir=${PREFIX}/share \
	--localstatedir=${PREFIX}/share
LIBS+=		-L${LOCALBASE}/lib

PAPERSIZE?=
.if ${PAPERSIZE:tl} == a4
RUN_DEPENDS+=	${LOCALBASE}/etc/papersize:print/papersize-default-a4
.endif

OPTIONS_DEFINE=NLS I18N EMACS
NO_OPTIONS_SORT=yes
OPTIONS_SUB=	yes
EMACS_DESC=Enable Emacs support
I18N_DESC=Enable I18N support

NLS_USES=		gettext
NLS_CONFIGURE_ENABLE=	nls
EMACS_USES=		emacs:build
EMACS_CONFIGURE_ON=	--with-lispdir=${LOCALBASE}/${EMACS_SITE_LISPDIR}

.include <bsd.port.options.mk>

.if ! ${PORT_OPTIONS:MEMACS}
CONFIGURE_ENV+=	EMACS=no
.endif

.if ${OPSYS} == FreeBSD && ${OSVERSION} > 1300512
CFLAGS+=	-DHAVE_MEMPCPY
.endif

post-patch:
	${REINPLACE_CMD} -e 's|^DESTDIR|#DESTDIR|' \
		`${FIND} ${WRKSRC} -name "Makefile.in"`

.if ${PORT_OPTIONS:MI18N}
#DISTFILES+=	${I18N_PACKAGE}${EXTRACT_SUFX}:i18n
DISTFILES=	${DISTNAME}${EXTRACT_SUFX} ${I18N_PACKAGE}${EXTRACT_SUFX}:i18n

pre-configure:
	cd ${WRKDIR}/${I18N_PACKAGE}/afm && \
		${ECHO_CMD} *.afm > afms.lst && \
		${MV} *.afm ${WRKSRC}/afm
	cd ${WRKDIR}/${I18N_PACKAGE}/fonts && \
		${MV} *.pfb ${WRKSRC}/fonts

post-configure:
	@cd ${WRKSRC}/fonts && { ${ECHO_CMD} ''; \
	${ECHO_CMD} "pfb_fonts =" *.pfb; } >> Makefile && \
	${REINPLACE_CMD} 's,^\(fonts_DATA = .*\),\1 $$(pfb_fonts),' Makefile
	@cd ${WRKSRC}/afm && { ${ECHO_CMD} ''; \
	${ECHO_CMD} "i18n_afms =" `cat ${WRKDIR}/${I18N_PACKAGE}/afm/afms.lst`; } >> Makefile && \
	${REINPLACE_CMD} 's,^\(all_afms = .*\),\1 $$(i18n_afms),' Makefile
.endif

post-install:
	cd ${WRKSRC}/doc && \
		${SETENV} ${MAKE_ENV} ${MAKE} ${.MAKEFLAGS} ${MAKE_ARGS} ${INSTALL_TARGET}
	${RM} ${STAGEDIR}${PREFIX}/lib/liba2ps.la

.include <bsd.port.mk>

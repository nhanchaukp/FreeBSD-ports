# pkg-help formatted with fmt 59 63

PORTNAME=	bind
PORTVERSION=	${ISCVERSION:S/-P/P/:S/b/.b/:S/a/.a/:S/rc/.rc/}
PORTREVISION=	0
CATEGORIES=	dns net
MASTER_SITES=	ISC/bind9/${ISCVERSION}
PKGNAMESUFFIX=	911
DISTNAME=	${PORTNAME}-${ISCVERSION}

MAINTAINER=	mat@FreeBSD.org
COMMENT=	BIND DNS suite with updated DNSSEC and DNS64

LICENSE=	MPL20
LICENSE_FILE=	${WRKSRC}/COPYRIGHT

DEPRECATED=	End of life, please migrate to a newer version of BIND9
EXPIRATION_DATE=	2022-03-31

LIB_DEPENDS=	libxml2.so:textproc/libxml2
RUN_DEPENDS=	bind-tools>0:dns/bind-tools

USES=	cpe libedit pkgconfig

# ISC releases things like 9.8.0-P1, which our versioning doesn't like
ISCVERSION=	9.11.36

CPE_VENDOR=	isc
CPE_VERSION=	${ISCVERSION:C/-.*//}
.if ${ISCVERSION:M*-*}
CPE_UPDATE=	${ISCVERSION:C/.*-//:tl}
.endif

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--localstatedir=/var --disable-linux-caps \
		--with-randomdev=/dev/random \
		--with-libxml2=${LOCALBASE} \
		--with-readline="-L${LOCALBASE}/lib -ledit" \
		--with-dlopen=yes \
		--with-gost=no \
		--without-python \
		--sysconfdir=${ETCDIR}
ETCDIR=		${PREFIX}/etc/namedb

CONFLICTS=	bind9[0-9][0-9] bind9-devel

SUB_FILES=	pkg-message named.conf
USE_RC_SUBR=	named

MAKE_JOBS_UNSAFE=	yes

PORTDOCS=	*

OPTIONS_DEFAULT=	SSL THREADS SIGCHASE IDN GSSAPI_NONE JSON \
			DLZ_FILESYSTEM LMDB RPZ_NSDNAME RPZ_NSIP TCP_FASTOPEN \
			FILTER_AAAA DNSTAP
OPTIONS_DEFINE=		ACCFDNS IDN LARGE_FILE JSON GEOIP \
			FIXED_RRSET SIGCHASE IPV6 THREADS FILTER_AAAA \
			RPZ_NSIP RPZ_NSDNAME DOCS \
			MINCACHE PORTREVISION QUERYTRACE LMDB DNSTAP \
			START_LATE TUNING_LARGE TCP_FASTOPEN

OPTIONS_RADIO=	CRYPTO
OPTIONS_RADIO_CRYPTO=	SSL NATIVE_PKCS11

OPTIONS_GROUP=		DLZ
OPTIONS_GROUP_DLZ=	DLZ_POSTGRESQL DLZ_MYSQL DLZ_BDB \
			DLZ_LDAP DLZ_FILESYSTEM DLZ_STUB
OPTIONS_SINGLE=		GSSAPI
OPTIONS_SINGLE_GSSAPI=	GSSAPI_BASE GSSAPI_HEIMDAL GSSAPI_MIT GSSAPI_NONE

OPTIONS_SUB=	yes

ACCFDNS_DESC=		Prefer DNS accept filter over generic one
CRYPTO_DESC=		Choose which crypto engine to use
DLZ_BDB_DESC=		DLZ BDB driver
DLZ_DESC=		Dynamically Loadable Zones
DLZ_FILESYSTEM_DESC=	DLZ filesystem driver
DLZ_LDAP_DESC=		DLZ LDAP driver
DLZ_MYSQL_DESC=		DLZ MySQL driver (no threading)
DLZ_POSTGRESQL_DESC=	DLZ Postgres driver
DLZ_STUB_DESC=		DLZ stub driver
DNSTAP_DESC=		Provides fast passive logging of DNS messages
FILTER_AAAA_DESC=	Enable filtering of AAAA records
FIXED_RRSET_DESC=	Enable fixed rrset ordering
GSSAPI_BASE_DESC=	Using Heimdal in base
GSSAPI_HEIMDAL_DESC=	Using security/heimdal
GSSAPI_MIT_DESC=	Using security/krb5
GSSAPI_NONE_DESC=	Disable
LARGE_FILE_DESC=	64-bit file support
LMDB_DESC=		Use LMDB for zone management
MINCACHE_DESC=		Use the mincachettl patch
NATIVE_PKCS11_DESC=	Use PKCS\#11 native API (**READ HELP**)
PORTREVISION_DESC=	Show PORTREVISION in the version string
QUERYTRACE_DESC=	Enable the very verbose query tracelogging
RPZ_NSDNAME_DESC=	Enable RPZ NSDNAME policy records
RPZ_NSIP_DESC=		Enable RPZ NSIP trigger rules
SIGCHASE_DESC=		dig/host/nslookup will do DNSSEC validation
SSL_DESC=		Build with OpenSSL (Required for DNSSEC)
START_LATE_DESC=	Start BIND late in the boot process (see help)
TCP_FASTOPEN_DESC=	RFC 7413 support
TUNING_LARGE_DESC=	Tune named for large systems (**READ HELP**)

ACCFDNS_EXTRA_PATCHES=	${PATCHDIR}/extrapatch-interfacemgr.c

DLZ_BDB_CONFIGURE_ON=	--with-dlz-bdb=yes
DLZ_BDB_USES=		bdb

DLZ_FILESYSTEM_CONFIGURE_ON=	--with-dlz-filesystem=yes

DLZ_LDAP_CONFIGURE_ON=	--with-dlz-ldap=yes
DLZ_LDAP_USE=		openldap=yes

DLZ_MYSQL_CONFIGURE_ON=	--with-dlz-mysql=yes
DLZ_MYSQL_PREVENTS=	THREADS
DLZ_MYSQL_USES=		mysql

DLZ_POSTGRESQL_CONFIGURE_ON=	--with-dlz-postgres=yes
DLZ_POSTGRESQL_USES=		pgsql

DLZ_STUB_CONFIGURE_ON=	--with-dlz-stub=yes

DNSTAP_CONFIGURE_ENABLE=	dnstap
DNSTAP_IMPLIES=		THREADS
DNSTAP_LIB_DEPENDS=	libfstrm.so:devel/fstrm \
			libprotobuf-c.so:devel/protobuf-c

FILTER_AAAA_CONFIGURE_ENABLE=	filter-aaaa

FIXED_RRSET_CONFIGURE_ENABLE=	fixed-rrset

GEOIP_CONFIGURE_WITH=	geoip2
GEOIP_LIB_DEPENDS=	libmaxminddb.so:net/libmaxminddb
GEOIP_IMPLIES=		THREADS

GSSAPI_BASE_CONFIGURE_ON=\
	--with-gssapi=${GSSAPIBASEDIR} KRB5CONFIG="${KRB5CONFIG}"
GSSAPI_BASE_USES=	gssapi

GSSAPI_HEIMDAL_CONFIGURE_ON=\
	--with-gssapi=${GSSAPIBASEDIR} KRB5CONFIG="${KRB5CONFIG}"
GSSAPI_HEIMDAL_USES=	gssapi:heimdal

GSSAPI_MIT_CONFIGURE_ON=\
	--with-gssapi=${GSSAPIBASEDIR} KRB5CONFIG="${KRB5CONFIG}"
GSSAPI_MIT_USES=	gssapi:mit

GSSAPI_NONE_CONFIGURE_ON=	--without-gssapi

IDN_CONFIGURE_OFF=	--without-libidn2
IDN_CONFIGURE_ON=	--with-libidn2=${LOCALBASE} ${ICONV_CONFIGURE_BASE}
IDN_LIB_DEPENDS=	libidn2.so:dns/libidn2
IDN_USES=		iconv

IPV6_CONFIGURE_ENABLE=	ipv6

JSON_CONFIGURE_WITH=	libjson=${LOCALBASE}
JSON_LIB_DEPENDS=	libjson-c.so:devel/json-c

LARGE_FILE_CONFIGURE_ENABLE=	largefile

LMDB_CONFIGURE_WITH=	lmdb=${LOCALBASE}
LMDB_LIB_DEPENDS=	liblmdb.so:databases/lmdb

MINCACHE_EXTRA_PATCHES=	${FILESDIR}/extrapatch-bind-min-override-ttl

NATIVE_PKCS11_CONFIGURE_ENABLE=	native-pkcs11
NATIVE_PKCS11_IMPLIES=	THREADS

QUERYTRACE_CONFIGURE_ENABLE=	querytrace

RPZ_NSDNAME_CONFIGURE_ENABLE=	rpz-nsdname

RPZ_NSIP_CONFIGURE_ENABLE=	rpz-nsip

SIGCHASE_CONFIGURE_ON=	STD_CDEFINES="-DDIG_SIGCHASE=1"

SSL_CONFIGURE_OFF=	--disable-openssl-version-check --without-openssl
SSL_CONFIGURE_ON=	--with-openssl=${OPENSSLBASE}
SSL_USES=		ssl

START_LATE_SUB_LIST=	NAMED_REQUIRE="SERVERS cleanvar" \
			NAMED_BEFORE="LOGIN"
START_LATE_SUB_LIST_OFF=NAMED_REQUIRE="NETWORKING ldconfig syslogd" \
			NAMED_BEFORE="SERVERS"

THREADS_CONFIGURE_ENABLE=	threads

TUNING_LARGE_IMPLIES=	THREADS
TUNING_LARGE_CONFIGURE_ON=	--with-tuning=large
TUNING_LARGE_CONFIGURE_OFF=	--with-tuning=default

.include <bsd.port.options.mk>

.if defined(WITH_DEBUG)
CONFIGURE_ARGS+=	--enable-symtable \
			--enable-developer
USES+=	perl5
USE_PERL5=	build
BUILD_DEPENDS+=	cmocka>0:sysutils/cmocka
# Developer mode needs ssl, always
.if !${PORT_OPTIONS:MSSL}
CONFIGURE_ARGS+=	--with-openssl=${OPENSSLBASE}
USES+=		ssl
.endif
.else
CONFIGURE_ARGS+=	--disable-symtable
.endif

.include <bsd.port.pre.mk>

.if ${SSL_DEFAULT} == base
SUB_LIST+=	ENGINES=/usr/lib/engines
.else
SUB_LIST+=	ENGINES=${LOCALBASE}/lib/engines
.endif

post-patch:
.for FILE in check/named-checkconf.8 named/named.8 nsupdate/nsupdate.1 \
	rndc/rndc.8
	@${REINPLACE_CMD} -e 's#/etc/named.conf#${ETCDIR}/named.conf#g' \
		-e 's#/etc/rndc.conf#${ETCDIR}/rndc.conf#g' \
		-e "s#/var\/run\/named\/named.pid#/var/run/named/pid#" \
		${WRKSRC}/bin/${FILE}
.endfor

.if ${PORTREVISION:N0}
post-patch-PORTREVISION-on:
	@${REINPLACE_CMD} -e '/EXTENSIONS/s#=$$#=_${PORTREVISION}#' \
		${WRKSRC}/version
.endif

post-patch-TCP_FASTOPEN-off:
	@${REINPLACE_CMD} -e 's/#define ISC_PLATFORM_HAVETFO 1/#undef ISC_PLATFORM_HAVETFO/' ${WRKSRC}/configure

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/mtree
	${MKDIR} ${STAGEDIR}${ETCDIR}
.for i in dynamic master slave working
	@${MKDIR} ${STAGEDIR}${ETCDIR}/$i
.endfor
	${INSTALL_DATA} ${WRKDIR}/named.conf ${STAGEDIR}${ETCDIR}/named.conf.sample
	${INSTALL_DATA} ${FILESDIR}/named.root ${STAGEDIR}${ETCDIR}
	${INSTALL_DATA} ${FILESDIR}/empty.db ${STAGEDIR}${ETCDIR}/master
	${INSTALL_DATA} ${FILESDIR}/localhost-forward.db ${STAGEDIR}${ETCDIR}/master
	${INSTALL_DATA} ${FILESDIR}/localhost-reverse.db ${STAGEDIR}${ETCDIR}/master
	${INSTALL_DATA} ${FILESDIR}/BIND.chroot.dist ${STAGEDIR}${PREFIX}/etc/mtree/BIND.chroot.dist.sample
	${INSTALL_DATA} ${FILESDIR}/BIND.chroot.local.dist ${STAGEDIR}${PREFIX}/etc/mtree/BIND.chroot.local.dist.sample
	${INSTALL_DATA} ${WRKSRC}/bin/rndc/rndc.conf \
		${STAGEDIR}${ETCDIR}/rndc.conf.sample

post-install-DOCS-on:
	${MKDIR} ${STAGEDIR}${DOCSDIR}/arm
	${INSTALL_DATA} ${WRKSRC}/doc/arm/*.html ${STAGEDIR}${DOCSDIR}/arm
	${INSTALL_DATA} ${WRKSRC}/doc/arm/Bv9ARM.pdf ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/CHANGES \
		${WRKSRC}/HISTORY* ${WRKSRC}/README* ${STAGEDIR}${DOCSDIR}

.include <bsd.port.post.mk>

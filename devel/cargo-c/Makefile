PORTNAME=	cargo-c
DISTVERSION=	0.9.8
PORTREVISION=	1
DISTVERSIONSUFFIX=	+cargo-0.60
CATEGORIES=	devel
MASTER_SITES=	CRATESIO
# XXX Teach USES=cargo to have proper default
DISTFILES=	${CARGO_DIST_SUBDIR}/${DISTNAME}${CARGO_CRATE_EXT}

MAINTAINER=	jbeich@FreeBSD.org
COMMENT=	Cargo C-ABI helpers

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libgit2.so:devel/libgit2 \
		libcurl.so:ftp/curl \
		libssh2.so:security/libssh2

USES=		cargo ssl
PLIST_FILES=	bin/cargo-capi \
		bin/cargo-cbuild \
		bin/cargo-cinstall \
		bin/cargo-ctest \
		${NULL}

CARGO_CRATES=	adler-1.0.2 \
		aho-corasick-0.7.18 \
		ansi_term-0.12.1 \
		anyhow-1.0.55 \
		arrayvec-0.5.2 \
		atty-0.2.14 \
		autocfg-1.1.0 \
		bitflags-1.3.2 \
		bitmaps-2.1.0 \
		bstr-0.2.17 \
		bytesize-1.1.0 \
		cargo-0.60.0 \
		cargo-platform-0.1.2 \
		cargo-util-0.1.2 \
		cbindgen-0.20.0 \
		cc-1.0.73 \
		cfg-if-1.0.0 \
		clap-2.34.0 \
		commoncrypto-0.2.0 \
		commoncrypto-sys-0.2.0 \
		core-foundation-0.9.3 \
		core-foundation-sys-0.8.3 \
		crates-io-0.33.1 \
		crc32fast-1.3.2 \
		crossbeam-utils-0.8.7 \
		crypto-hash-0.3.4 \
		curl-0.4.42 \
		curl-sys-0.4.52+curl-7.81.0 \
		either-1.6.1 \
		env_logger-0.9.0 \
		fastrand-1.7.0 \
		filetime-0.2.15 \
		flate2-1.0.22 \
		fnv-1.0.7 \
		foreign-types-0.3.2 \
		foreign-types-shared-0.1.1 \
		form_urlencoded-1.0.1 \
		fwdansi-1.1.0 \
		git2-0.13.25 \
		git2-curl-0.14.1 \
		glob-0.3.0 \
		globset-0.4.8 \
		hashbrown-0.11.2 \
		heck-0.3.3 \
		hermit-abi-0.1.19 \
		hex-0.3.2 \
		hex-0.4.3 \
		home-0.5.3 \
		humantime-2.1.0 \
		idna-0.2.3 \
		ignore-0.4.18 \
		im-rc-15.0.0 \
		indexmap-1.8.0 \
		instant-0.1.12 \
		itertools-0.10.3 \
		itoa-1.0.1 \
		jobserver-0.1.24 \
		lazy_static-1.4.0 \
		lazycell-1.3.0 \
		libc-0.2.119 \
		libgit2-sys-0.12.26+1.3.0 \
		libnghttp2-sys-0.1.7+1.45.0 \
		libssh2-sys-0.2.23 \
		libz-sys-1.1.3 \
		log-0.4.14 \
		matches-0.1.9 \
		memchr-2.4.1 \
		miniz_oxide-0.4.4 \
		miow-0.3.7 \
		num_cpus-1.13.1 \
		once_cell-1.9.0 \
		opener-0.5.0 \
		openssl-0.10.38 \
		openssl-probe-0.1.5 \
		openssl-src-111.17.0+1.1.1m \
		openssl-sys-0.9.72 \
		os_info-3.2.0 \
		percent-encoding-2.1.0 \
		pkg-config-0.3.24 \
		proc-macro-error-1.0.4 \
		proc-macro-error-attr-1.0.4 \
		proc-macro2-1.0.36 \
		quote-1.0.15 \
		rand_core-0.5.1 \
		rand_xoshiro-0.4.0 \
		redox_syscall-0.2.10 \
		regex-1.5.4 \
		regex-automata-0.1.10 \
		regex-syntax-0.6.25 \
		remove_dir_all-0.5.3 \
		rustc-workspace-hack-1.0.0 \
		rustfix-0.6.0 \
		ryu-1.0.9 \
		same-file-1.0.6 \
		schannel-0.1.19 \
		semver-1.0.6 \
		serde-1.0.136 \
		serde_derive-1.0.136 \
		serde_ignored-0.1.2 \
		serde_json-1.0.79 \
		shell-escape-0.1.5 \
		sized-chunks-0.6.5 \
		socket2-0.4.4 \
		strip-ansi-escapes-0.1.1 \
		strsim-0.8.0 \
		structopt-0.3.26 \
		structopt-derive-0.4.18 \
		syn-1.0.86 \
		tar-0.4.38 \
		tempfile-3.3.0 \
		termcolor-1.1.2 \
		textwrap-0.11.0 \
		thread_local-1.1.4 \
		tinyvec-1.5.1 \
		tinyvec_macros-0.1.0 \
		toml-0.5.8 \
		typenum-1.15.0 \
		unicode-bidi-0.3.7 \
		unicode-normalization-0.1.19 \
		unicode-segmentation-1.9.0 \
		unicode-width-0.1.9 \
		unicode-xid-0.2.2 \
		url-2.2.2 \
		utf8parse-0.2.0 \
		vcpkg-0.2.15 \
		vec_map-0.8.2 \
		version_check-0.9.4 \
		vte-0.10.1 \
		vte_generate_state_changes-0.1.1 \
		walkdir-2.3.2 \
		winapi-0.3.9 \
		winapi-i686-pc-windows-gnu-0.4.0 \
		winapi-util-0.1.5 \
		winapi-x86_64-pc-windows-gnu-0.4.0

post-patch:
	@${REINPLACE_CMD} -e 's,libdir.join("pkgconfig,prefix.join("libdata/pkgconfig,' \
		${WRKSRC}/src/install.rs

.include <bsd.port.mk>

# Created by: Hiroyuki Iwatsuki <don@na.rim.or.jp>

PKGNAMEPREFIX=	ruby-

MAINTAINER=	lev@FreeBSD.org
COMMENT=	Ruby bindings for version control system

USES+=		compiler:c11
USE_RUBY=	yes

PORTREVISION_114=	0
PORTREVISION_LTS=	0

SVN_BUILD_BINDINGS=	yes

.include "${.CURDIR}/../../devel/subversion/Makefile.addons"

CATEGORIES+=	ruby

CONFIGURE_ARGS+=	--without-gnome-keyring \
			--without-kwallet \
			--with-apxs=no

ALL_TARGET=	swig-rb-lib swig-rb
INSTALL_TARGET=	install-swig-rb

CFLAGS+=	-fdeclspec

.include <bsd.port.post.mk>

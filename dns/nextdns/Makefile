PORTNAME=	nextdns
PORTVERSION=	1.37.7
CATEGORIES=	dns security

MAINTAINER=	rs@nextdns.io
COMMENT=	NextDNS DNS53 to DNS over HTTPS proxy

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	ca_root_nss>=3.35:security/ca_root_nss

USES=		go:modules
USE_GITHUB=	yes
GH_TAGNAME=	v1.37.7
GH_TUPLE=	\
		cespare:xxhash:v1.1.0:cespare_xxhash/vendor/github.com/cespare/xxhash \
		denisbrodbeck:machineid:v1.0.1:denisbrodbeck_machineid/vendor/github.com/denisbrodbeck/machineid \
		golang:net:60bc85c4be6d:golang_net/vendor/golang.org/x/net \
		golang:sys:63515b42dcdf:golang_sys/vendor/golang.org/x/sys \
		hashicorp:golang-lru:v0.5.4:hashicorp_golang_lru/vendor/github.com/hashicorp/golang-lru \
		vishvananda:netlink:v1.1.0:vishvananda_netlink/vendor/github.com/vishvananda/netlink \
		vishvananda:netns:2eb08e3e575f:vishvananda_netns/vendor/github.com/vishvananda/netns

GO_TARGET=	.:${PREFIX}/sbin/nextdns

SUB_FILES=	pkg-message

PLIST_FILES=	sbin/nextdns

.include <bsd.port.mk>

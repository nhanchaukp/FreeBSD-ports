PORTNAME=	swaync
DISTVERSIONPREFIX=	v
PORTVERSION=	0.4
CATEGORIES=	x11

MAINTAINER=	jbeich@FreeBSD.org
COMMENT=	Simple Wayland notification daemon with GTK panel

LICENSE=	GPLv3+
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	valac:lang/vala
LIB_DEPENDS=	libjson-glib-1.0.so:devel/json-glib \
		libgtk-layer-shell.so:x11-toolkits/gtk-layer-shell \
		libhandy-1.so:x11-toolkits/libhandy

USES=		compiler:c11 gnome localbase:ldflags meson pkgconfig
USE_GITHUB=	yes
USE_GNOME=	gdkpixbuf2 gtk30 introspection:build
GH_ACCOUNT=	ErikReider
GH_PROJECT=	SwayNotificationCenter

post-patch:
# Extract (snapshot) version from the port instead of meson.build
	@${REINPLACE_CMD} -i .nogit -e 's/git.found()/false/' \
		-e '/project_version/s/@0@/${DISTVERSIONFULL}/' \
		${WRKSRC}/src/meson.build
# Let @sample handle default files under etc/
	@${REINPLACE_CMD} -e "s,'/',get_option('prefix')," \
		-e "/output.*json/s/'[^']*/&.sample/" \
		-e "/inst.*css/s/'[^']*/&', rename: &.sample/1" \
		${WRKSRC}/src/meson.build

.include <bsd.port.mk>

PORTNAME=	gtk4
PORTVERSION=	3.5.1
CATEGORIES=	x11-toolkits rubygems
MASTER_SITES=	RG

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Ruby binding of GTK+ 4.x

LICENSE=	LGPL21+
LICENSE_FILE=	${WRKSRC}/COPYING.LIB

RUN_DEPENDS=	rubygem-atk>=${PORTVERSION}:accessibility/rubygem-atk \
		rubygem-gdk_pixbuf2>=${PORTVERSION}:graphics/rubygem-gdk_pixbuf2 \
		rubygem-gdk4>=${PORTVERSION}:x11-toolkits/rubygem-gdk4 \
		rubygem-gio2>=${PORTVERSION}:devel/rubygem-gio2 \
		rubygem-pango>=${PORTVERSION}:x11-toolkits/rubygem-pango

USES=		gem gnome
USE_GNOME=	gtk40
USE_RUBY=	yes

NO_ARCH=	yes

.include <bsd.port.mk>

# Created by: Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	flipper-ui
PORTVERSION=	0.24.0
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Rack middleware that provides a fully featured web interface

LICENSE=	MIT

RUN_DEPENDS=	rubygem-erubi>=1.0.0<2.0.0:www/rubygem-erubi \
		rubygem-flipper>=${PORTVERSION}<0.25:devel/rubygem-flipper \
		rubygem-rack>=1.4,3<3,3:www/rubygem-rack \
		rubygem-rack-protection>=1.5.3<2.2.0:www/rubygem-rack-protection \
		rubygem-sanitize>=0<7:textproc/rubygem-sanitize

USES=		gem
USE_RUBY=	yes

NO_ARCH=	yes

.include <bsd.port.mk>

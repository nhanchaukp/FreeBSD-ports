# Created by: Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	rails-i18n
PORTVERSION=	7.0.2
CATEGORIES=	devel rubygems
MASTER_SITES=	RG
PKGNAMESUFFIX=	-rails70

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Set of common locale data and translations for Rails

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/MIT-LICENSE.txt

RUN_DEPENDS=	rubygem-i18n>=0.7,2<2,2:devel/rubygem-i18n \
		rubygem-railties70>=6.0.0<8:www/rubygem-railties70

USES=		gem
USE_RUBY=	yes

NO_ARCH=	yes

.include <bsd.port.mk>

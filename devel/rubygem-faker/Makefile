PORTNAME=	faker
PORTVERSION=	2.19.0
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Library for generating fake data: names, addresses, phone numbers

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/License.txt

RUN_DEPENDS=	rubygem-i18n>=1.6,2<2,2:devel/rubygem-i18n

USES=		gem
USE_RUBY=	yes

CONFLICTS_INSTALL=	py*-Faker

NO_ARCH=	yes

PLIST_FILES=	bin/faker

.include <bsd.port.mk>

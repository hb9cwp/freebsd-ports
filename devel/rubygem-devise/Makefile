# Created by: rpsfa@rit.edu
# $FreeBSD$

PORTNAME=	devise
PORTVERSION=	4.2.0
PORTREVISION=	1
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	ruby@FreeBSD.org
COMMENT=	Flexible authentication solution for Rails with Warden

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/MIT-LICENSE

RUN_DEPENDS=	rubygem-bcrypt>=3.0:security/rubygem-bcrypt \
		rubygem-orm_adapter>=0.1:devel/rubygem-orm_adapter \
		rubygem-thread_safe>=0.1:devel/rubygem-thread_safe \
		rubygem-responders>=0:www/rubygem-responders \
		rubygem-warden>=1.2.3:devel/rubygem-warden \
		rubygem-railties4>=4.1.1:www/rubygem-railties4 \
		rubygem-responders>=0:www/rubygem-responders

NO_ARCH=	yes
USE_RUBY=	yes
USES=		gem

BROKEN_RUBY23=	yes

post-patch:
	@${REINPLACE_CMD} -e 's|, "test/rails_app/config/routes.rb"||' ${WRKSRC}/${PORTNAME}.gemspec

.include <bsd.port.mk>

# Created by: Ryan Steinmetz <zi@FreeBSD.org>
# $FreeBSD$

PORTNAME=	mod_webauth
PORTVERSION=	4.7.0
CATEGORIES=	www
MASTER_SITES=	http://webauth.stanford.edu/dist/
DISTNAME=	webauth-${PORTVERSION}

MAINTAINER=	apache@FreeBSD.org
COMMENT=	Apache module for authenticating users with Kerberos v5

LIB_DEPENDS=	libcurl.so:ftp/curl \
		libsasl2.so:security/cyrus-sasl2

USES=		libtool pkgconfig
USE_APACHE=	22+
USE_OPENLDAP=	yes
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-ldap-lib=${LOCALBASE}/lib \
		--with-ldap-include=${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
INSTALL_TARGET=	install-strip

post-patch:
	@${REINPLACE_CMD} -e 's|libdir)/pkgconfig|prefix)/libdata/pkgconfig|' \
		${WRKSRC}/Makefile.in ${WRKSRC}/Makefile.am
	@${REINPLACE_CMD} -e '/typedef int sig_atomic_t/d' \
		${WRKSRC}/portable/system.h

.include <bsd.port.mk>

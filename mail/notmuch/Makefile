# Created by: DarwinSurvivor <darwinsurvivor@gmail.com>
# $FreeBSD$

PORTNAME=	notmuch
PORTVERSION=	0.22.1
CATEGORIES=	mail
MASTER_SITES=	http://notmuchmail.org/releases/

MAINTAINER=	mp39590@gmail.com
COMMENT=	Thread-based email index, search, and tagging application

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING-GPL-3

BUILD_DEPENDS=	c++filt:devel/binutils
LIB_DEPENDS=	libgmime-2.6.so:mail/gmime26 \
		libxapian.so:databases/xapian-core \
		libtalloc.so:devel/talloc

BROKEN_powerpc64=	Does not build

OPTIONS_DEFINE=	BASH DOXYGEN EMACS MANPAGES RUBY ZSH
EMACS_DESC=	Install EMACS lisp files (requires emacs)
OPTIONS_SUB=	yes

BASH_BUILD_DEPENDS=	bash-completion>=1.90:shells/bash-completion
BASH_RUN_DEPENDS=	${BASH_BUILD_DEPENDS}
BASH_CONFIGURE_WITH=	bash-completion
DOXYGEN_CONFIGURE_WITH=	docs
DOXYGEN_BUILD_DEPENDS=	doxygen:devel/doxygen
EMACS_CONFIGURE_WITH=	emacs
EMACS_CONFIGURE_ON=	--emacslispdir=${PREFIX}/${EMACS_SITE_LISPDIR} \
			--emacsetcdir=${PREFIX}/${EMACS_SITE_LISPDIR}
EMACS_USE=	EMACS=yes
MANPAGES_BUILD_DEPENDS=	sphinx-build:textproc/py-sphinx
RUBY_USE=	RUBY=yes
ZSH_CONFIGURE_WITH=	zsh-completion

HAS_CONFIGURE=	yes
USES=		gmake pkgconfig python:build
USE_GNOME=	glib20
CONFIGURE_ARGS=	--prefix=${PREFIX} --mandir=${MANPREFIX}/man
USE_LDCONFIG=	yes

MAKE_ENV+=		PYTHONCMD=${PYTHON_CMD}

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/notmuch
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/libnotmuch.so.4.3.0

.include <bsd.port.mk>

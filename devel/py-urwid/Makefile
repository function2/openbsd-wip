# $OpenBSD: Makefile,v 1.14 2013/03/11 10:50:27 espie Exp $

COMMENT =	console user interface library for python

MODPY_EGG_VERSION = 1.1.0
DISTNAME =	urwid-${MODPY_EGG_VERSION}
PKGNAME =	py-${DISTNAME}
CATEGORIES =	devel

HOMEPAGE =	http://excess.org/urwid/

# GPL
PERMIT_PACKAGE_CDROM =	Yes

MASTER_SITES =	${HOMEPAGE}

TEST_DEPENDS =	devel/py-gobject \
		lang/python/${MODPY_VERSION},-tests \
		devel/py-twisted/core

MODULES =	lang/python
MODPY_SETUPTOOLS = Yes
MODPY_BADEGGS =	urwid

PKG_ARCH =	*

WANTLIB +=	${MODPY_WANTLIB} pthread

.include <bsd.port.mk>

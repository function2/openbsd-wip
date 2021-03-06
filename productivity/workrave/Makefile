# $OpenBSD: Makefile,v 1.38 2015/03/27 08:14:14 ajacoutot Exp $

COMMENT=		reminder program for prevention of RSI

DISTNAME=		workrave-1.10.1
CATEGORIES=		productivity x11

HOMEPAGE=		http://www.workrave.org/

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += ICE SM X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi
WANTLIB += Xinerama Xrandr Xrender Xss Xtst atk-1.0 atk-bridge-2.0
WANTLIB += atkmm-1.6 atspi c cairo cairo-gobject cairomm-1.0 dbus-1
WANTLIB += dbus-glib-1 epoxy expat ffi fontconfig freetype gconf-2
WANTLIB += gdk-3 gdk_pixbuf-2.0 gdkmm-3.0 gio-2.0 giomm-2.4 glib-2.0
WANTLIB += glibmm-2.4 gmodule-2.0 gobject-2.0 graphite2 gstreamer-0.10
WANTLIB += gthread-2.0 gtk-3 gtkmm-3.0 harfbuzz lzma m pango-1.0
WANTLIB += pangocairo-1.0 pangoft2-1.0 pangomm-1.4 pcre pixman-1
WANTLIB += png pthread pthread-stubs sigc-2.0 stdc++ xcb xcb-render
WANTLIB += xcb-shm xml2 z

SHARED_LIBS +=		workrave-private-1.0      0.0

MASTER_SITES=		${MASTER_SITE_SOURCEFORGE:=workrave/}

BUILD_DEPENDS=		devel/py-cheetah \
			${MODGNU_AUTOCONF_DEPENDS} \
                        ${MODGNU_AUTOMAKE_DEPENDS}

RUN_DEPENDS=		devel/desktop-file-utils \
			x11/gtk+3,-guic
LIB_DEPENDS=		devel/gconf2 \
			multimedia/gstreamer-0.10/core \
			x11/dbus-glib \
			x11/gtk3mm

MODULES=		devel/gettext \
			lang/python \
			textproc/intltool

USE_GMAKE=		Yes

CONFIGURE_STYLE=	gnu
AUTOCONF_VERSION =	2.69
AUTOMAKE_VERSION =	1.11
CONFIGURE_ARGS+=	--disable-xml \
			--disable-pulse \
			--enable-dbus

# gnome support requires libpanelapplet
CONFIGURE_ARGS+=	--disable-gnome2 \
			--disable-gnome3
CONFIGURE_ENV=		CPPFLAGS="-I${LOCALBASE}/include -I${X11BASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib -L${X11BASE}/lib"

pre-configure:
	@cd ${WRKSRC}; env AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION} autoreconf

.include <bsd.port.mk>

# Created by: Maxim Sobolev <sobomax@FreeBSD.org>
# $FreeBSD$

PORTNAME=	sdl
PORTVERSION=	1.2.15
PORTREVISION=	10
PORTEPOCH=	2
CATEGORIES=	devel
MASTER_SITES=	http://www.libsdl.org/release/
DISTNAME=	SDL-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Cross-platform multimedia development API

LICENSE=	LGPL21
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	nasm:devel/nasm

USES=		gmake iconv libtool localbase:ldflags pathfix pkgconfig
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ENV=	ac_cv_header_libusbhid_h=no
CONFIGURE_ARGS=	--disable-alsa --disable-alsatest \
		--disable-arts --disable-video-directfb --disable-video-ggi

EXAMPLES=	test/*.c test/*.bmp test/*.dat test/*.xbm test/*.wav
DOCS=		BUGS CREDITS README README-SDL.txt WhatsNew docs.html

OPTIONS_DEFINE=		AALIB DOCS EXAMPLES OPENGL SVGALIB X11
OPTIONS_DEFAULT=	AALIB OPENGL OSS X11
OPTIONS_GROUP=		AUDIO
OPTIONS_GROUP_AUDIO=	ESOUND NAS OSS PULSEAUDIO SNDIO

AUDIO_DESC=		Audio backend

.if exists(/usr/lib/libvgl.so)
OPTIONS_DEFINE+=	VGL
VGL_DESC=		Video Graphics Lib support
OPTIONS_DEFAULT+=	VGL
.endif

AALIB_CONFIGURE_ENABLE=		video-aalib
AALIB_LIB_DEPENDS=		libaa.so:graphics/aalib
ESOUND_USE=			GNOME=esound
ESOUND_CONFIGURE_ENABLE=	esd esdtest
NAS_CONFIGURE_ENABLE=		nas
NAS_LIB_DEPENDS=		libaudio.so:audio/nas
OPENGL_CONFIGURE_ENABLE=	video-opengl
OPENGL_USE=			GL=yes
OSS_CONFIGURE_ENABLE=		oss
PULSEAUDIO_CONFIGURE_ENABLE=	pulseaudio
PULSEAUDIO_LIB_DEPENDS=		libpulse-simple.so:audio/pulseaudio
SNDIO_CONFIGURE_ENABLE=		sndio
SNDIO_LIB_DEPENDS=		libsndio.so:audio/sndio
SVGALIB_CONFIGURE_ENABLE=	video-svga
SVGALIB_LIB_DEPENDS=		libvga.so:graphics/svgalib
VGL_CONFIGURE_ENABLE=		video-vgl
VGL_VARS=			PKGMESSAGE=pkg-message.vgl
X11_CONFIGURE_ENABLE=		video-x11
X11_USE=			XORG=x11,xrender,xrandr,xextproto

post-patch:
	@${REINPLACE_CMD} -e '/EXTRA_LDFLAGS/s/-liconv/${ICONV_LIB}/' \
		${WRKSRC}/configure

post-patch-SNDIO-on:
	@${MKDIR} ${WRKSRC}/src/audio/sndio
	@${CP} ${FILESDIR}/SDL_sndioaudio.* ${WRKSRC}/src/audio/sndio

post-install:
	@${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/libSDL-1.2.so.0.11.4

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${DOCS:S,^,${WRKSRC}/,} ${STAGEDIR}${DOCSDIR}/
	cd ${WRKSRC} && ${COPYTREE_SHARE} docs ${STAGEDIR}${DOCSDIR}/ "! -regex .*/man3.*"

post-install-EXAMPLES-on:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${EXAMPLES:S,^,${WRKSRC}/,} ${STAGEDIR}${EXAMPLESDIR}/

.include <bsd.port.mk>

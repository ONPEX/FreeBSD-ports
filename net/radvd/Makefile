# Created by: Patrick Li <pat@databits.net>
# $FreeBSD$

PORTNAME=	radvd
PORTVERSION=	1.9.1
CATEGORIES=	net ipv6
MASTER_SITES=	http://www.litech.org/radvd/dist/

MAINTAINER=	farrokhi@FreeBSD.org
COMMENT=	Linux/BSD IPv6 router advertisement daemon

LICENSE=	RADVD
LICENSE_NAME=	RADVD License
LICENSE_FILE=	${WRKSRC}/COPYRIGHT
LICENSE_PERMS=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept

LIB_DEPENDS=	libdaemon.so:devel/libdaemon

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--program-transform-name=
USES=		gmake pkgconfig
USE_RC_SUBR=	radvd

PORTDOCS=	CHANGES COPYRIGHT INTRO.html README TODO

post-install:
	${INSTALL_DATA} ${WRKSRC}/radvd.conf.example ${STAGEDIR}${PREFIX}/etc
	${INSTALL} -d ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S.^.${WRKSRC}/.} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>

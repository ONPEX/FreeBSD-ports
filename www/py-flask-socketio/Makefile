# $FreeBSD$

PORTNAME=	Flask-SocketIO
PORTVERSION=	2.8.6
CATEGORIES=	www python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	mmokhi@FreeBSD.org
COMMENT=	Socket.IO integration for Flask applications

LICENSE=	MIT

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}Flask>=0:www/py-flask \
		${PYTHON_PKGNAMEPREFIX}gevent-websocket>=0:www/py-gevent-websocket \
		${PYTHON_PKGNAMEPREFIX}python-engineio>=1.0.0:devel/py-python-engineio \
		${PYTHON_PKGNAMEPREFIX}python-socketio>=1.5.0:devel/py-python-socketio

USES=		python
USE_PYTHON=	distutils autoplist

.include <bsd.port.mk>

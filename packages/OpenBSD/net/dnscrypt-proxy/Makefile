# $OpenBSD$

COMMENT-main=		secure communications between a DNS client and resolver
COMMENT-plugins=	example plugins for dnscrypt-proxy

V=			1.1.0

DISTNAME=		dnscrypt-proxy-${V}
CATEGORIES=		net
MASTER_SITES=		https://github.com/downloads/opendns/dnscrypt-proxy/

HOMEPAGE=		http://dnscrypt.org

MAINTAINER=		Frank Denis <dnscrypt@pureftpd.org>

# BSD
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

MULTI_PACKAGES=		-main -plugins

PKGNAME-main=		dnscrypt-proxy-${V}
PKGNAME-plugins=	dnscrypt-proxy-plugins-${V}

commonWANTLIB=		c execinfo kvm m

WANTLIB-main=		${commonWANTLIB} ltdl
WANTLIB-plugins=	${commonWANTLIB} crypto ldns

commonLIB_DEPENDS=	devel/libexecinfo

LIB_DEPENDS-main=	${commonLIB_DEPENDS} devel/libtool,-ltdl
LIB_DEPENDS-plugins=	${commonLIB_DEPENDS} net/ldns/libldns

BUILD_DEPENDS-plugins=	devel/libtool

BUILD_DEPENDS=		archivers/gtar
TAR=			${LOCALBASE}/bin/gtar

CONFIGURE_STYLE=	gnu

CONFIGURE_ARGS+=	--enable-plugins --enable-plugins-root

DOCS=			README-PLUGINS.markdown \
			README.markdown \
			TECHNOTES

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/dnscrypt-proxy
	cd ${WRKSRC}; ${INSTALL_DATA} ${DOCS} ${PREFIX}/share/doc/dnscrypt-proxy

.include <bsd.port.mk>

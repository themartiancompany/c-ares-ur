# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>
# Maintainer: Daniel J Griffiths <ghost1227@archlinux.us>

pkgname=c-ares
pkgver=1.7.4
pkgrel=1
pkgdesc='C library that performs DNS requests and name resolves asynchronously'
arch=('i686' 'x86_64')
url='http://c-ares.haxx.se/'
license=('custom')
depends=('glibc')
options=('!libtool')
source=(http://c-ares.haxx.se/${pkgname}-${pkgver}.tar.gz
        LICENSE)
md5sums=('dd71e8f07d9f3c837e12a5416d1b7f73'
         'c69f2042941b708ce3e7121424d0b7e6')

build() {
	cd ${srcdir}/${pkgname}-${pkgver}

	./configure --prefix=/usr --enable-shared || return 1
	make || return 1
}

package() {
	cd ${srcdir}/${pkgname}-${pkgver}
	make DESTDIR=${pkgdir} install || return 1

	install -Dm644 ${srcdir}/LICENSE \
		${pkgdir}/usr/share/licenses/${pkgname}/LICENSE || return 1
}

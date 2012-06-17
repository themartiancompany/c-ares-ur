# Maintainer: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=c-ares
pkgver=1.9.0
pkgrel=1
pkgdesc='C library that performs DNS requests and name resolves asynchronously'
arch=('i686' 'x86_64')
url='http://c-ares.haxx.se/'
license=('custom')
depends=('glibc')
options=('!libtool')
source=("http://c-ares.haxx.se/download/$pkgname-$pkgver.tar.gz"{,.asc}
        'LICENSE')
md5sums=('c1a61a5a9db15129ba538f724de50ded'
         '5cfadabe6c9cb1e0aa879803129bcfe3'
         'c69f2042941b708ce3e7121424d0b7e6')

build() {
	cd "$srcdir/$pkgname-$pkgver"

	./configure --prefix=/usr --enable-shared
	make
}

package() {
	cd "$srcdir/$pkgname-$pkgver"

	make DESTDIR="$pkgdir" install
	install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

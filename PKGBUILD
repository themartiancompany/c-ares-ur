# Maintainer: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=c-ares
pkgver=1.10.0
pkgrel=1
pkgdesc='C library that performs DNS requests and name resolves asynchronously'
arch=('i686' 'x86_64')
url='http://c-ares.haxx.se/'
license=('custom')
depends=('glibc')
options=('!libtool')
source=("http://c-ares.haxx.se/download/$pkgname-$pkgver.tar.gz"{,.asc}
        'LICENSE')
md5sums=('1196067641411a75d3cbebe074fd36d8'
         'SKIP'
         'c69f2042941b708ce3e7121424d0b7e6')

build() {
  cd "$pkgname-$pkgver"

  ./configure --prefix=/usr --enable-shared
  make
}

package() {
  cd "$pkgname-$pkgver"

  make DESTDIR="$pkgdir" install
  install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

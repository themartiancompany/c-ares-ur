# Maintainer: Jeff Mickey <jeff@archlinux.org>
# Maintainer: Vinay S Shastry <vinayshastry@gmail.com>
pkgname=c-ares
pkgver=1.5.2
pkgrel=1
pkgdesc="c-ares is a C library that performs DNS requests and name resolves asynchronously"
url="http://daniel.haxx.se/projects/c-ares/"
arch=('i686' 'x86_64')
license=('MIT')
depends=()
source=(http://daniel.haxx.se/projects/c-ares/$pkgname-$pkgver.tar.gz)
options=('!libtool')

build() {
  cd $startdir/src/$pkgname-$pkgver
  ./configure --prefix=/usr
  make || return 1
  make DESTDIR=$startdir/pkg install
}

md5sums=('23adb3729e09879cd2147b31ea5a986e')
sha1sums=('67a64ca1eab60dabfd462b833216ada3a0de7ffa')

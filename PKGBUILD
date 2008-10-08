# Maintainer: Jeff Mickey <jeff@archlinux.org>
# Maintainer: Vinay S Shastry <vinayshastry@gmail.com>
pkgname=c-ares
pkgver=1.5.3
pkgrel=1
pkgdesc="c-ares is a C library that performs DNS requests and name resolves asynchronously"
url="http://daniel.haxx.se/projects/c-ares/"
arch=('i686' 'x86_64')
license=('MIT')
depends=()
options=('!libtool')
source=(http://daniel.haxx.se/projects/c-ares/$pkgname-$pkgver.tar.gz LICENSE)
md5sums=('ec202543a8cb86647f52e1ed4b5c0b37' '8d3b474b934eff15d006a754b7e45216')
sha1sums=('885fa291d7ae7d825c732b38ae147d5f83cc1904' '07d7104fc2d16e9232bd89e5a2fe28735444a6c3')

build() {
  cd $startdir/src/$pkgname-$pkgver
  ./configure --prefix=/usr
  make || return 1
  make DESTDIR=$startdir/pkg install
  install -D -m644 ../LICENSE $startdir/pkg/usr/share/licenses/$pkgname/LICENSE
}

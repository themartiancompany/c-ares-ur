# Maintainer: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=c-ares
pkgver=1.13.0
pkgrel=1
pkgdesc='C library that performs DNS requests and name resolves asynchronously'
arch=('x86_64')
url='https://c-ares.haxx.se/'
license=('custom')
depends=('glibc')
source=("https://c-ares.haxx.se/download/$pkgname-$pkgver.tar.gz"{,.asc}
        'LICENSE')
sha512sums=('4a7942e754673f5b8d55a7471e31b0f390e8324b14c12077580c956147fad4d165c7fe8a3190199b1add95c710ceeb1a7957706d4f0d6299d39c5dddc719bd9d'
            'SKIP'
            '55e8607392c5f82ed85e3580fa632dfdc2dcd0b1a5e918dc61d00532c15c11ecb709f6007b65805c1fbe8fcd21ee794c9e4a9638c97ac1f4960b2654010a4d0a')
validpgpkeys=('27EDEAF22F3ABCEB50DB9A125CC908FDB71E12C2'   # Daniel Stenberg
              '914C533DF9B2ADA2204F586D78E11C6B279D5C91')  # Daniel Stenberg

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

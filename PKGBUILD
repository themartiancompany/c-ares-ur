# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=c-ares
pkgver=1.22.0
pkgrel=1
pkgdesc="A C library for asynchronous DNS requests"
arch=(x86_64)
url="https://c-ares.haxx.se/"
license=(MIT)
depends=(glibc)
makedepends=(cmake)
provides=(libcares.so)
source=(https://github.com/$pkgname/$pkgname/releases/download/${pkgname//-}-${pkgver//./_}/$pkgname-$pkgver.tar.gz{,.asc})
sha512sums=('b84b774090bbeae7ad2eabeb223a12474e42f2efcc4e2209fcda260b1fe29337549eb7827eb7f75475fade65b6e1ab719abdae0ff543309c1914aa9cef65cd01'
            'SKIP')
b2sums=('0f70c2cfe9e5076eaa97262a9b34d915d755618dc89884a2d743a0d47827bb99d2a1d1bb655aff92d8c85a19a4420a1e685d91f82b9f7a55cc2feb5daa27fd41'
        'SKIP')
validpgpkeys=('27EDEAF22F3ABCEB50DB9A125CC908FDB71E12C2') # Daniel Stenberg <daniel@haxx.se>

build() {
  local cmake_options=(
    -B build
    -D CMAKE_INSTALL_PREFIX=/usr
    -D CMAKE_BUILD_TYPE=None
    -S $pkgname-$pkgver
    -W no-dev
  )
  cmake "${cmake_options[@]}"
  cmake --build build --verbose
}

check() {
  ctest --test-dir build --output-on-failure
}

package() {
  DESTDIR="$pkgdir" cmake --install build
  install -vDm 644 $pkgname-$pkgver/LICENSE.md -t "$pkgdir/usr/share/licenses/$pkgname/"
  install -vDm 644 $pkgname-$pkgver/{AUTHORS,CHANGES,{CONTRIBUTING,README}.md,RELEASE-NOTES} -t "$pkgdir/usr/share/doc/$pkgname/"
}

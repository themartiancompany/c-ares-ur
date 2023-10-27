# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=c-ares
pkgver=1.21.0
pkgrel=1
pkgdesc="A C library for asynchronous DNS requests"
arch=(x86_64)
url="https://c-ares.haxx.se/"
license=(MIT)
depends=(glibc)
makedepends=(cmake)
provides=(libcares.so)
source=(https://github.com/$pkgname/$pkgname/releases/download/${pkgname//-}-${pkgver//./_}/$pkgname-$pkgver.tar.gz{,.asc})
sha512sums=('c526b0a28d8ea1c6a53215dfd52e8250c968513a667c5414459d97d46288da7e7a2193d757fc78225e56c6684b3d30e756dd3e5a31917e996c871773a34892ea'
            'SKIP')
b2sums=('708933603dfc6c0286e798b3244eb9d8bce500acb915a255b82e00133509e5c2ceaad6b9b4cd081fcd9193b64fdb72e4e7ff6deeca8eb1744124ab9239cacac0'
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

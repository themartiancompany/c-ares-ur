# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=c-ares
pkgver=1.25.0
pkgrel=1
pkgdesc="A C library for asynchronous DNS requests"
arch=(x86_64)
url="https://c-ares.org/"
license=(MIT)
depends=(glibc)
makedepends=(cmake)
provides=(libcares.so)
source=(
  $url/download/$pkgname-$pkgver.tar.gz
  $url/download/$pkgname-$pkgver.tar.gz.asc
)
sha512sums=('f73ffc45c17f1e952ea5fae8a1d9e1508427f21c821ff470ff0b728cc4a1e21d1274f95d9192c22f704bc7e0f58a633608cfdc1704dfe8950902fdfc3dfa2e1c'
            'SKIP')
b2sums=('a4f4b493e1331ade27504238c3e520e1ffaa525baf99442c88de3aeda1eb06a12ec804a5f0f699fb8acd469ccd2b3d08f5c32b4d01d50cfdc31097665087fce9'
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

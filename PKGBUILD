# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=c-ares
pkgver=1.20.1
pkgrel=1
pkgdesc="A C library for asynchronous DNS requests"
arch=(x86_64)
url="https://c-ares.haxx.se/"
license=(MIT)
depends=(glibc)
makedepends=(cmake)
provides=(libcares.so)
source=(https://github.com/$pkgname/$pkgname/releases/download/${pkgname//-}-${pkgver//./_}/$pkgname-$pkgver.tar.gz{,.asc})
sha512sums=('83400fb276ebcf16dfe6f43d56ca87839d132b5a0544420eda9fa148eb85468b3f215593fcefc2a7a3a8ed8b0d4ef093ed99616a4e466b01f6913934240539e4'
            'SKIP')
b2sums=('44d160e04dcbd78f0ad7c1f2eb3f34ff07017fd9b5c4bc12b81b123022297adccfff45f43630f8c73afdfd9424ff6ee9fb96c627405ec486c8d78bb0c7e518ca'
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

# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Dave Reisner <dreisner@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

_os="$( \
  uname \
    -o)"
pkgname=c-ares
pkgver=1.26.0
pkgrel=1
pkgdesc="A C library for asynchronous DNS requests"
arch=(
  x86_64
  aarch64
  arm
)
url="https://c-ares.org/"
license=(MIT)
depends=()
[[ "${_os}" == "GNU/Linux" ]] && \
  depends+=(
    glibc
  )
makedepends=(cmake)
provides=(libcares.so)
source=(
  $url/download/$pkgname-$pkgver.tar.gz{,.asc}
)
sha512sums=('81657b8b9840a565b04ecf87ef8f0fc3192a9594808e47aed5e5bbebf2b5f0066b0cd5fae70f0fe70b68d428b4cc75fba22d2ae7683c6d0f87979c414c072af1'
            'SKIP')
b2sums=('9bcbb321b31518fdd3481447e1bba733dbf0eabd1876aa0fec6737888fd176b837c64e6b22ae5754a905f0fd1591d4fd516db558fafae92cc2684ad7e0c29f63'
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
  install -vDm 644 $pkgname-$pkgver/{AUTHORS,CHANGES,{CONTRIBUTING,README,RELEASE-NOTES}.md} -t "$pkgdir/usr/share/doc/$pkgname/"
}

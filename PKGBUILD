pkgname=wiiu-curl
pkgver=8.16.0
pkgrel=2
pkgdesc='Library for transferring data with URLs'
arch=('any')
url='https://github.com/dkosmari/curl/tree/wiiu'
license=('The curl license')
options=(!strip libtool staticlibs)
makedepends=('wiiu-pkg-config' 'dkp-toolchain-vars')
depends=('wut' 'ppc-zlib' 'wiiu-mbedtls')
groups=('wiiu-portlibs')

source=("https://github.com/dkosmari/curl/releases/download/$pkgname-$pkgver/$pkgname-$pkgver.tar.gz")

build() {
  cd $pkgname-$pkgver

  ./configure --disable-silent-rules --host=powerpc-eabi --enable-wiiu --prefix=$DEVKITPRO/portlibs/wiiu --disable-shared --disable-ipv6 --disable-unix-sockets --disable-socketpair --disable-manual --with-mbedtls --with-ca-path=/vol/storage_mlc01/sys/title/0005001b/10054000/content/scerts --without-libpsl --enable-websockets --enable-verbose --disable-docs --enable-threaded-resolver CFLAGS="-Os -ffunction-sections"

  make -C lib
}

package() {
  cd $pkgname-$pkgver

  make DESTDIR="$pkgdir" -C lib install
  make DESTDIR="$pkgdir" -C include install
  make DESTDIR="$pkgdir" install-binSCRIPTS install-pkgconfigDATA

  install -Dm644 COPYING "$pkgdir"${PORTLIBS_PREFIX}/licenses/$pkgname/COPYING
}

sha256sums=('76dc64b32a7fc5db5ac55bced6aa56f2e58e221d01eddf67b9c4bae4729da3b0')

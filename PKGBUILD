license=('BSD')
arch=('x86_64')
pkgname=libev
pkgver=4.33
pkgrel=1
pkgdesc="A full-featured and high-performance event loop"
depends=('glibc')
url="https://software.schmorp.de/pkg/libev.html"
source=(http://dist.schmorp.de/${pkgname}/${pkgname}-${pkgver}.tar.gz)
sha1sums=('133587b89c34dba0b3a2d2a90ba59f6748f6c368')

build() {
 cd ${pkgname}-${pkgver}

  ./configure --prefix=/usr
  make
}

check() {
  cd ${pkgname}-${pkgver}
  make check
}

package() {
  cd ${pkgname}-${pkgver}

  make DESTDIR="${pkgdir}" install

  # fix conflict with libevent
  rm "${pkgdir}"/usr/include/event.h

  install -Dm644 LICENSE "${pkgdir}"/usr/share/licenses/${pkgname}/LICENSE
}

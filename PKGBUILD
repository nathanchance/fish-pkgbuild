# Maintainer: Kaiting Chen <kaitocracy@gmail.com>
# Maintainer:  Bartłomiej Piotrowski <nospam@bpiotrowski.pl>
# Contributor: Abhishek Dasgupta <abhidg@gmail.com>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Jan Fader <jan.fader@web.de>

pkgname=fish
pkgver=2.0b2
pkgrel=1
pkgdesc='Smart and user friendly shell intended mostly for interactive use'
arch=('i686' 'x86_64')
url='http://ridiculousfish.com/shell/'
license=('GPL2')
depends=('python')
makedepends=('doxygen')
install=fish.install
source=($pkgname-$pkgver.tar.gz::http://ridiculousfish.com/shell/files/fishfish.tar.gz)
md5sums=('ebe5fe17f6925b9142aadc8ebae5fba1')

build() {
  cd "$srcdir"/fishfish
  autoconf
  ./configure --prefix=/usr \
              --sysconfdir=/etc  \
              --without-xsel
  make
}

package() {
  cd "$srcdir"/fishfish
  make DESTDIR="$pkgdir" install

  # compress man pages
  find "$pkgdir"/usr/share/fish/man/ -type f | xargs gzip -9
}

# Maintainer: Kaiting Chen <kaitocracy@gmail.com>
# Maintainer:  Bartłomiej Piotrowski <nospam@bpiotrowski.pl>
# Contributor: Abhishek Dasgupta <abhidg@gmail.com>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Jan Fader <jan.fader@web.de>

pkgname=fish
pkgver=2.0.0
pkgrel=1
pkgdesc='Smart and user friendly shell intended mostly for interactive use'
arch=('i686' 'x86_64')
url='http://fishshell.com/'
license=('GPL2')
depends=('python2')
makedepends=('doxygen' 'python')
install=fish.install
source=(fish-$pkgver.tar.gz::http://fishshell.com/files/$pkgver/fish.tar.gz)
md5sums=('fe5907e6af61607d4128ce891a1f6501')

build() {
  set -x
  cd fish
  autoconf
  ./configure --prefix=/usr \
              --sysconfdir=/etc \
              --without-xsel
  make
}

package() {
  cd fish
  make DESTDIR="$pkgdir" install

  # use python2
  find "$pkgdir"/usr/share/fish/tools/ -type f -exec sed -e "1s|python|python2|" -i {} \;
}

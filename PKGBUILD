# Maintainer:  Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Kaiting Chen <kaitocracy@gmail.com>
# Contributor: Abhishek Dasgupta <abhidg@gmail.com>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Jan Fader <jan.fader@web.de>

pkgname=fish
pkgver=2.1.2
pkgrel=1
pkgdesc='Smart and user friendly shell intended mostly for interactive use'
arch=('i686' 'x86_64')
url='http://fishshell.com/'
license=('GPL2')
depends=('bc' 'gcc-libs' 'inetutils' 'ncurses' 'which')
optdepends=('python: for manual page completion parser and web configuration tool')
makedepends=('doxygen')
install=fish.install
source=($pkgname-$pkgver.tar.gz::https://github.com/fish-shell/fish-shell/archive/$pkgver.tar.gz
        fish-2.1.1-grep-options-is-deprecated.patch)
md5sums=('855389f9ed4cbe9290ca8d45b9b23093'
         '0c94b1ca8c54ed1a03b551f9b84160e5')

prepare() {
  cd fish-shell-$pkgver
  patch -p1 -i ../fish-2.1.1-grep-options-is-deprecated.patch

  echo $pkgver > version
  autoconf -i
}

build() {
  cd fish-shell-$pkgver
  ./configure --prefix=/usr \
    --sysconfdir=/etc
  make
}

package() {
  make -C fish-shell-$pkgver DESTDIR="$pkgdir" install
}

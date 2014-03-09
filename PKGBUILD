# Maintainer:  Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Kaiting Chen <kaitocracy@gmail.com>
# Contributor: Abhishek Dasgupta <abhidg@gmail.com>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Jan Fader <jan.fader@web.de>

pkgname=fish
pkgver=2.1.0
pkgrel=2
pkgdesc='Smart and user friendly shell intended mostly for interactive use'
arch=('i686' 'x86_64')
url='http://fishshell.com/'
license=('GPL2')
depends=('bc' 'gcc-libs' 'inetutils' 'ncurses')
optdepends=('python: for manual page completion parser and web configuration tool')
install=fish.install
source=(http://fishshell.com/files/$pkgver/fish-$pkgver.tar.gz)
md5sums=('3a29aebde522b8f52d9975d7423db99e')

build() {
  cd $pkgname-$pkgver
  ./configure --prefix=/usr \
    --sysconfdir=/etc \
    --without-xsel
  make
}

package() {
  make -C $pkgname-$pkgver DESTDIR="$pkgdir" install
}

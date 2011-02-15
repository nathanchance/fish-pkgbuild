# Maintainer: Kaiting Chen <kaitocracy@gmail.com>
# Contributor: Abhishek Dasgupta <abhidg@gmail.com>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Jan Fader <jan.fader@web.de>

pkgname=fish
pkgver=1.23.1
pkgrel=4
pkgdesc="User friendly shell intended mostly for interactive use"
arch=('i686' 'x86_64')
url="http://fishshell.com/"
license=("GPL" "LGPL" "BSD" "MIT")
depends=('ncurses' 'bc')
makedepends=('doxygen')
install=fish.install
source=(http://fishshell.com/files/$pkgver/$pkgname-$pkgver.tar.bz2)
md5sums=('ead6b7c6cdb21f35a3d4aa1d5fa596f1')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  ./configure --prefix=/usr --sysconfdir=/etc  \
     --docdir=/usr/share/doc/fish --without-xsel
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir" install
  install -D -m644 user_doc/html/license.html "$pkgdir/usr/share/licenses/$pkgname/license.html"
}

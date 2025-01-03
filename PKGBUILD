# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Kaiting Chen <kaitocracy@gmail.com>
# Contributor: Abhishek Dasgupta <abhidg@gmail.com>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Jan Fader <jan.fader@web.de>

pkgname=fish
_repo=$pkgname-shell
pkgver=4.0b1
pkgrel=0
pkgdesc='Smart and user friendly shell intended mostly for interactive use'
url='https://fishshell.com/'
arch=('x86_64')
license=('GPL-2.0-only AND BSD-3-Clause AND ISC AND MIT AND PSF-2.0')
depends=('glibc' 'gcc-libs' 'ncurses' 'pcre2')
optdepends=('python: man page completion parser / web config tool'
            'pkgfile: command-not-found hook')
makedepends=('cargo' 'cmake' 'git' 'python-sphinx' 'jq')
checkdepends=('expect' 'procps-ng')
install=fish.install
options=(!lto) # breaks the build and it is not necessary
backup=(etc/fish/config.fish)
source=(git+https://github.com/$_repo/$_repo)
sha256sums=('SKIP')
sha512sums=('SKIP')

pkgver() {
  git -C $_repo describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd $_repo

  export CXXFLAGS+=" ${CPPFLAGS}"
  cmake \
    -B build \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_SYSCONFDIR=/etc \
    -DBUILD_DOCS=True \
    -Wno-dev
  make -C build VERBOSE=1
}

check() {
  cd $_repo

  make -C build test
}

package() {
  cd $_repo

  make -C build DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:

# Maintainer: speps <speps at aur dot archlinux dot org>

_name=bml
pkgname=bml-git
pkgver=0.8.0.44f7edc
pkgrel=1
pkgdesc="Buzztrax machine loader (former Buzztard)"
arch=('i686' 'x86_64')
url="http://www.buzztard.org"
license=('LGPL')
makedepends=('git')
provides=("bml=$pkgver")
conflicts=('bml' 'bml-svn')
replaces=('bml-svn')
options=('!libtool' '!strip')
source=("$pkgname::git+https://github.com/Buzztrax/bml.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  echo $(awk -F '[][]' '/AC_INIT/{print $4}' configure.ac).$(git rev-parse --short HEAD)
}

build() {
  cd "$srcdir/$pkgname"
  ./autogen.sh
  ./configure --prefix=/usr \
              --enable-static=no \
              --enable-debug
  make
}

package() {
  cd "$srcdir/$pkgname"
  make DESTDIR="$pkgdir/" install
}

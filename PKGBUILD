# Maintainer: Stefan Husmann <stefan-husmann@t-online.de>

pkgname=le-git
pkgver=583.a56e5fd
pkgrel=1
pkgdesc="A text editor in memorial to Norton Editor with block and binary operations - git version"
arch=('i686' 'x86_64')
url="https://directory.fsf.org/wiki/Le_editor"
license=('GPL3')
depends=('gcc-libs' 'ncurses')
makedepends=('git')
provides=('le')
conflicts=('le')
source=(git://git.sv.gnu.org/gnulib git://github.com/lavv17/le.git)
md5sums=('SKIP' 'SKIP')
_gitname="le"

pkgver() {
  cd $srcdir/$_gitname
  printf "%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)" | sed 's|-|.|g'
}

build() {
  cd "$srcdir/$_gitname"
  chmod 770 $srcdir/gnulib/gnulib-tool
  PATH=$PATH:$srcdir/gnulib
  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$_gitname"
  make DESTDIR="$pkgdir/" install
}

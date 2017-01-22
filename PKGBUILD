pkgname=hstr
pkgver=1.21
pkgrel=1
pkgdesc="A command line utility that brings improved BASH command completion from the history. It aims to make completion easier and more efficient than Ctrl-r."
arch=('x86_64')
url="https://github.com/dvorka/hstr"
license=('Apache')
makedepends=('readline' 'ncurses')
depends=('readline')
source=(https://github.com/dvorka/$pkgname/archive/${pkgver}.tar.gz)
md5sums=('c6304f8424fb1b445a4391a60550a042')

build() {
    cd "hstr-$pkgver/dist"
    ./1-dist.sh
    cd ..
    sed -i -e "s#<ncursesw/curses.h>#<curses.h>#g" src/include/hstr_curses.h
    sed -i -e "s#<ncursesw/curses.h>#<curses.h>#g" src/hstr.c
    ./configure --prefix=/usr
    make
}

package() {
    cd "hstr-$pkgver"
    make DESTDIR="$pkgdir/" install
}

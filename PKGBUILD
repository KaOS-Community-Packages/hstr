pkgname=hstr
pkgver=1.19
pkgrel=1
pkgdesc="A command line utility that brings improved BASH command completion from the history. It aims to make completion easier and more efficient than Ctrl-r."
arch=('x86_64')
url="https://github.com/dvorka/hstr"
license=('Apache')
makedepends=('readline' 'ncurses')
depends=('readline')
source=(https://github.com/dvorka/hstr/releases/download/$pkgver/hh-$pkgver-src.tgz)
md5sums=('8129d6cca6153587afc3bfa72c83ffd2')

build() {
    cd "hstr/dist"
    ./1-dist.sh
    cd ..
    sed -i -e "s#<ncursesw/curses.h>#<curses.h>#g" src/include/hstr_curses.h
    sed -i -e "s#<ncursesw/curses.h>#<curses.h>#g" src/hstr.c
    ./configure --prefix=/usr
    make
}

package() {
    cd "hstr"
    make DESTDIR="$pkgdir/" install
}

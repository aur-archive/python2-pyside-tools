# Maintainer: Hugo Osvaldo Barrera <hugo@barrera.io>
# Contributor: Matthias Maennich <arch@maennich.net>
# Contributor: Massimiliano Torromeo <massimiliano.torromeo@gmail.com>

pkgname=python2-pyside-tools
_gitname=Tools
pkgver=0.2.15
pkgrel=2
_pyver=2.7
pkgdesc="UI Compiler (pyside-uic) plus Qt Resource Compiler (pyside-rcc4) for PySide."
arch=('i686' 'x86_64')
license=('LGPL')
url="http://www.pyside.org"
depends=('python2-pyside' 'python2')
replaces=('pyside-tools')
makedepends=('cmake' 'python2-shiboken')
source=("https://github.com/PySide/Tools/archive/${pkgver}.tar.gz")
md5sums=('e542b9536bd9d35599ede225c9311cc8')

build(){
    cd $srcdir/${_gitname}-$pkgver
    sed -e "s/python/python2/g" -i pyside-uic
    mkdir -p build && cd build
    _pyver=2.7
    cmake ../ -DCMAKE_INSTALL_PREFIX=/usr \
              -DCMAKE_BUILD_TYPE=Release \
	      -DSHIBOKEN_PYTHON_SUFFIX=-python$_pyver \
	      -DPYTHON_EXECUTABLE=/usr/bin/python$_pyver \
              -DQT_QMAKE_EXECUTABLE=qmake-qt4 \
              -DPYTHON_BASENAME=-python$_pyver \
              -DPYTHON_SUFFIX=-python2.7
    make
}

package(){
    cd $srcdir/${_gitname}-$pkgver/build
	make DESTDIR=$pkgdir install
}


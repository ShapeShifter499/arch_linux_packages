# Maintainer: Joey Dumont <joey.dumont@gmail.com>
# Contributor: Lucas Hermann Negri <lucashnegri at gmail dot com>

pkgname=armadillo
pkgver=6.300.2
pkgrel=1
pkgdesc="C++ linear algebra library"
arch=('i686' 'x86_64')
url="http://arma.sourceforge.net/"
license=('MPL 2.0')
depends=('lapack' 'blas' 'arpack' 'superlu=4.3')
optdepends=('hdf5: HDF5 output'
            'cuda: NVBLAS support'
	    'acml-cblas: ACML support')
makedepends=('cmake')
source=("http://downloads.sourceforge.net/sourceforge/arma/$pkgname-$pkgver.tar.gz")
install=("armadillo.install")
sha512sums=('00365514fd018a54c29c356fbfa1a558b5a8f709d4ada409f2edbdc6cfa71768064ea6e2242a956cd6ed7c7806dce48a835c149870e2e5d044db53c3321ee550')

build() {
  if [ "$CARCH" == "x86_64" ]; then
    ARMA64LIBDIR="-DINSTALL_LIB_DIR:PATH=/usr/lib"
  fi

  cd "${srcdir}/$pkgname-$pkgver"
  cmake  $ARMA64LIBDIR -DCMAKE_INSTALL_PREFIX:PATH=/usr .
  make
}

package() {
  cd "${srcdir}/$pkgname-$pkgver"
  make DESTDIR="${pkgdir}" install
  install -D -m644 LICENSE.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
      

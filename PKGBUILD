# Maintainer: Dominik Fuchs <dominik.fuchs@wur.nl>
# Contributor: Marcelo Avalos Tejeda <marcelo.avalos@gmail.com>

pkgname=ggobi
pkgver=2.1.9
pkgrel=1
pkgdesc="GGobi is an open source visualization program for exploring high-dimensional data. It provides highly dynamic and interactive graphics."
url="http://www.ggobi.org/"
arch=('i686' 'x86_64')
license='GPL'
#depends=('cairo' 'gtk2' 'graphviz' 'libxml2')
depends=('cairo' 'gtk2' 'libxml2')
source=(http://www.ggobi.org/downloads/$pkgname-$pkgver.tar.bz2
#	$pkgname-$pkgver-graphviz.patch
        ggobi.desktop
        ggobi.png
)

md5sums=('b579861f157dfc6c5669604859352eb4'
#         'c0846e8c612e440c6b82493433284086'
         '263e058d21a99719b9f558490d8e1916'
         '0fb7af6434a15ec086e3ce094c92b511')

build() {
  cd $srcdir/$pkgname-$pkgver

#  patch -Np1 -i ${srcdir}/$pkgname-$pkgver-graphviz.patch || return 1

  ./configure --prefix=/usr
  make || return 1
  make DESTDIR=$pkgdir install
  make ggobirc
  mkdir -p $pkgdir/etc/xdg/ggobi 
  install -D -m644 ggobirc $pkgdir/etc/xdg/ggobi/ggobirc
  
  cd $startdir
  mkdir -p pkg/usr/share/applications pkg/usr/share/pixmaps
  install -D -m644 ggobi.png $pkgdir/usr/share/pixmaps/ggobi.png
  install -D -m644 ggobi.desktop $pkgdir/usr/share/applications/ggobi.desktop
}

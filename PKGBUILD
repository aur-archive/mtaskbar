# Contributor: Douglas Soares de Andrade <dsandrade@gmail.com>
# Contributor: failure <ljofre@gmail.com>

pkgname=mtaskbar
pkgver=0.7
pkgrel=1
pkgdesc="A modified TaskBar for the KDE 3.4 kicker panel which supports thumbnail images of application windows"
arch=('i686' 'x86_64')
url="http://www.uni-weimar.de/~wolff3/index_taskbar.html"
license=('GPL')
depends=('x-server' 'kdelibs3')
options=('libtool')
source=(http://www.uni-weimar.de/~wolff3/kdelook/$pkgname-$pkgver.tar.bz2 mtaskbar-gcc4.patch mtaskbar-desktop.patch)
md5sums=('53fdd1b7cd97b3f66c68d2de9d507914' 'be529ce0fcd7c946140f3aec84471a65'\
         '8d2f41507ec8d5395031bb7ecc8a75fd')

build() {
	. /etc/profile.d/qt.sh
	export PATH=$QTDIR/bin:$PATH
 	# Using the patches to make it work against gcc>=4. Thanks gentoo
	# people for the patches ! :o)
	patch -Np0 < ../mtaskbar-gcc4.patch
	patch -Np0 < ../mtaskbar-desktop.patch
	
	cd $startdir/src/$pkgname-$pkgver/mtaskbar
	./configure --prefix=/opt/kde
	make || return 1
	make DESTDIR=$startdir/pkg install
} 

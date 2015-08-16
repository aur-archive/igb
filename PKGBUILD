# Contributor: Vadym Abramchuk <abramm@gmail.com>
pkgname=igb
pkgver=3.4.8
pkgrel=1
pkgdesc="Intel igb server adapters driver"
license=(GPL)
arch=(i686 x86_64)
backup=(etc/modprobe.d/igb.conf)
makedepends=(linux-headers)
install="igb.install"
url='http://downloadcenter.intel.com/detail_desc.aspx?agr=Y&DwnldID=13663'
source=(http://downloadmirror.intel.com/13663/eng/$pkgname-$pkgver.tar.gz igb.install igb.modprobe)
md5sums=('36bd0eface2761577f52d84d5c5b78ea'
         'fa6d8f3dc144930203914930262b4e1b'
         'daa91423878f549a157c93aa75dee891')


build() {
	cd $srcdir/$pkgname-$pkgver/src

	make || return 1
	# Install in updates so we leave original igb
	install -D -m 644 igb.ko $pkgdir/lib/modules/`uname -r`/updates/igb.ko || return 1
	install -D -m 644 $srcdir/igb.modprobe $pkgdir/etc/modprobe.d/igb.conf
}

# Old Maintainer: lolo <hl.cd@laposte.net>
# Maintainer: archist <archist@gmx.de>

pkgname=cpupowerd
pkgver=0.2.1
pkgrel=6
pkgdesc="A daemon which controls the frequency and voltage of CPUs. This userland program adjusts the frequency and voltage (including over-/undervolting) according to the CPUs load. Currently it supports only AMD K8 processors like Athlon(64) (X2), Sempron ...."
arch=(i686 x86_64)
url="http://sourceforge.net/projects/cpupowerd"
license=('GPL2')
depends=('bash')
replaces=('cpupower')
optdepends=('mprime')
install="$pkgname.install"
backup=(etc/cpupowerd.conf)
options=()
source=("http://downloads.sourceforge.net/project/${pkgname}/${pkgname}/${pkgver}/${pkgname}-${pkgver}.tar.gz"
	'cpupowerd'
	'cpupowerd.conf'
	'cpupowerd.service'
	'modules-cpupowerd.conf')
md5sums=('219b95de8c53622a9fdb8b5bfeba29e3'
	'5a8402e23df004c8ab9a0a6b5d0e5b24'
	'9f2fc44c109364931931444cd6f5c72b'
	'55cfcdbe47b6511b06eadc2d9c58bd65'
	'cb4610d6f7a894100b60e92c6c9a402c')

build() {
  cd $startdir/src/$pkgname-$pkgver/src
  make || return 1
}

package() {
  mkdir -p  ${pkgdir}/usr/bin
  install -m 755 $startdir/src/$pkgname-$pkgver/src/cpupowerd ${pkgdir}/usr/bin
  mkdir -p ${pkgdir}/usr/share/cpupowerd
  install -m 755 $startdir/src/$pkgname-$pkgver/README ${pkgdir}/usr/share/cpupowerd
  mkdir -p  ${pkgdir}/etc
  install -m 755 $startdir/cpupowerd.conf ${pkgdir}/etc
  mkdir -p  ${pkgdir}/etc/rc.d
  install -m 755 $startdir/cpupowerd ${pkgdir}/etc/rc.d
  mkdir -p  ${pkgdir}/etc/systemd/system
  install -m 755 $startdir/cpupowerd.service ${pkgdir}/etc/systemd/system
  mkdir -p  ${pkgdir}/etc/modules-load.d/
  install -m 755 $startdir/modules-cpupowerd.conf ${pkgdir}/etc/modules-load.d/cpupowerd.conf
}

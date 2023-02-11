## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Chupligin Sergey (NeoChapay) <neochapay@gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt5-lipstick
pkgver=0.48
pkgrel=1
pkgdesc="QML toolkit for homescreen creation"
arch=('x86_64' 'aarch64')
url="https://github.com/nemomobile-ux/lipstick"
license=('LGPL-2.1-only')
depends=('qt5-sensors-sensorfw'
	    'qt5-wayland'
	    'nemo-keepalive'
	    'libresourceqt'
	    'libsystemd'
	    'mce-headers'
	    'libmce-qt>=1.5.0'
	    'libngf-qt'
	    'nemo-qml-plugin-devicelock'
	    'nemo-qml-plugin-systemsettings'
	    'pulseaudio'
	    'pulseaudio-modules-nemo'
	    'pulseaudio-policy-enforcement'
	    'bluez-qt')

makedepends=('qt5-tools'
	'doxygen'
	'graphviz'
	'make'
	'pkgconfig')

source=("${url}/archive/refs/tags/$pkgver.tar.gz"
	"https://github.com/sailfishos-mirror/dbus-glib/archive/d42176ae4763e5288ef37ea314fe58387faf2005.tar.gz")
sha256sums=('8aadfd9afc02193bde9ab2ddc89276015dc7c44156e9aea3ce9eb3ef4a2f2056'
	"f4c28d4740ac90863082e81c869e5178d25238b179747984faf0509e40d1afef")

build() {
  cd "lipstick-${pkgver}"
  cp ../dbus-glib-d42176ae4763e5288ef37ea314fe58387faf2005/dbus-gmain.* src/3rdparty/dbus-gmain/
  mkdir -p build
  cd build
  qmake VERSION=${pkgver} ..
  make
}

package() {
  cd "lipstick-${pkgver}"
  cd build
  make -j 1 INSTALL_ROOT="${pkgdir}" install
}

## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Chupligin Sergey (NeoChapay) <neochapay@gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt5-lipstick
pkgver=0.46.2
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
	    'bluez-qt'
	    'glacier-settings-developermode')

makedepends=('qt5-tools'
	'doxygen'
	'graphviz'
	'make'
	'pkgconfig')

source=("${url}/archive/refs/tags/$pkgver.tar.gz"
	"https://github.com/sailfishos-mirror/dbus-glib/archive/d42176ae4763e5288ef37ea314fe58387faf2005.tar.gz")
sha256sums=('c3c9136d20071ebcd9cbcd6e9fc7934095bb6dd3fe5af1ee2bb00ceb5b4c9c44'
	"f4c28d4740ac90863082e81c869e5178d25238b179747984faf0509e40d1afef")

build() {
  cd "lipstick-${pkgver}"
  cp ../dbus-glib-d42176ae4763e5288ef37ea314fe58387faf2005/dbus-gmain.* src/3rdparty/dbus-gmain/
  mkdir -p build
  cd build
  qmake ..
  make
}

package() {
  cd "lipstick-${pkgver}"
  cd build
  make -j 1 INSTALL_ROOT="${pkgdir}" install
}

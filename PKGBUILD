## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Chupligin Sergey (NeoChapay) <neochapay@gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt5-lipstick
pkgver=0.47
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
	"https://github.com/sailfishos-mirror/dbus-glib/archive/refs/heads/dbus-gmain.tar.gz")
sha256sums=('8a7a9ce5b8a578572645fb3c144464b6ac03e5c6b05d76fa8e63fb6ebe0db5c3'
	"a130b3bbf5745d430d0eca331a29048ab66d678d4267c87f4f26855678940ebf")

build() {
  cd "lipstick-${pkgver}"
  cp ../dbus-glib-dbus-gmain/dbus-gmain.* src/3rdparty/dbus-gmain/
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

## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Chupligin Sergey (NeoChapay) <neochapay@gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt5-lipstick
pkgver=0.45.3
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
	    'libmce-qt'
	    'libngf-qt'
	    'nemo-qml-plugin-devicelock'
	    'nemo-qml-plugin-systemsettings'
	    'pulseaudio'
	    'bluez-qt')

makedepends=('qt5-tools'
	'doxygen'
	'graphviz'
	'make'
	'pkgconfig')

source=("${url}/archive/refs/tags/$pkgver.tar.gz")
sha256sums=('54742bec30e702494aea6bd03edff86bd09960387773828a9dfcd47e69fe96bc')

build() {
  cd "lipstick-${pkgver}"
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

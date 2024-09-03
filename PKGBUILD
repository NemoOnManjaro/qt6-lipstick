## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Chupligin Sergey (NeoChapay) <neochapay@gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

_reponame=lipstick
pkgname=qt6-${_reponame}
pkgver=1.2.7
pkgrel=2
pkgdesc="QML toolkit for homescreen creation"
arch=('x86_64' 'aarch64')
url="https://github.com/nemomobile-ux/${_reponame}"
license=('LGPL-2.1-only')
depends=(
        'qt6-sensors-sensorfw'
        'qt6-wayland'
        'nemo-keepalive'
        'libresourceqt'
        'libsystemd'
        'libmce-qt>=1.5.1'
        'libngf-qt6'
        'nemo-qml-plugin-devicelock>=0.3.9'
        'nemo-qml-plugin-systemsettings'
        'nemo-qml-plugin-connectivity>=0.2.15'
        'pulseaudio'
        'pulseaudio-modules-nemo'
        'pulseaudio-policy-enforcement'
        'bluez-qt>=6.0')

makedepends=('qt6-tools'
    'mce-headers'
    'doxygen'
    'graphviz'
    'make'
    'pkgconfig'
    'timed'
    'cmake')

source=("${url}/archive/refs/tags/$pkgver.tar.gz"
	"https://github.com/sailfishos-mirror/dbus-glib/archive/d42176ae4763e5288ef37ea314fe58387faf2005.tar.gz")
sha256sums=('9011404b68a4bbde34e99f8fa9ada7ac15c55978b7144d08be99c23ed5ec5bc9'
	"f4c28d4740ac90863082e81c869e5178d25238b179747984faf0509e40d1afef")

build() {
  cd "${srcdir}/${_reponame}-${pkgver}"
  cp ../dbus-glib-d42176ae4763e5288ef37ea314fe58387faf2005/dbus-gmain.* src/3rdparty/dbus-gmain/
  mkdir -p build
  cd build
  cmake ../  -DCMAKE_INSTALL_PREFIX:PATH='/usr'
  make  all
}

package() {
  cd "${srcdir}/${_reponame}-${pkgver}/build"
  make DESTDIR="$pkgdir" install
}
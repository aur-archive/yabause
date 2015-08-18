# Maintainer : Harley Laue <losinggeneration@gmail.com>
# Contributor: Hyacinthe Cartiaux <hyacinthe.cartiaux@free.fr>
# Contributor: Anton Shestakov <engored*ya.ru>
# Contributor: Tiago Camargo <tcamargo@gmail.com>
# Contributor: robb_force <robb_force@holybuffalo.net>
pkgname=yabause
pkgver=0.9.12
pkgrel=3
pkgdesc='A Sega Saturn emulator.'
url='http://yabause.org/'
license=('GPL')
arch=('i686' 'x86_64')
makedepends=('cmake' 'mesa' 'glu')
depends=('sdl' 'qt4' 'openal' 'freeglut')
source=("http://downloads.sourceforge.net/${pkgname}/${pkgname}-${pkgver}.tar.gz")
md5sums=('c7876c04489f8a1b59b3166598084cb8')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  [ -e build ] && rm -rf build
  mkdir build
  cd build
  cmake \
    -DCMAKE_BUILD_TYPE=RelWithDebInfo \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DQT_QMAKE_EXECUTABLE=/usr/bin/qmake-qt4 \
    -DYAB_PORTS=qt \
    -DYAB_MULTIBUILD=OFF \
    -DYAB_NETWORK=ON \
    -DYAB_OPTIMIZED_DMA=on \
    -DYAB_PERKEYNAME=ON \
    ..

  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}/build"
  make DESTDIR="${pkgdir}" install
}

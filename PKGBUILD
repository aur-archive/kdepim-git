# Maintainer anex <lane.wiscombe[@]gmail.com>

pkgname=kdepim-git
_pkgname=kdepim
arch=('x86_64')
pkgver=r89998.2a0f1bf
pkgrel=2
pkgdesc="Project that aims to bring together anything to do with personal information management."
url="http://www.kde.org"
license=('GPL' 'LGPL' 'FDL')
depends=('grantlee-qt5' 'phonon-qt5' 'qt5-tools' 'prison-frameworks-git' 'libkgapi-frameworks-git'
         'kdelibs4support-git' 'kwallet-git' 'knewstuff-git' 'kcmutils-git' 'kdewebkit-git' 'karchive-git' 
         'knotifyconfig-git' 'kconfig-git' 'khtml-git' 'kservice-git' 'kdbusaddons-git' 'kauth-git' 
         'ktexteditor-git' 'kdnssd-git' 'kcodecs-git' 'kglobalaccel-git' 'sonnet-git' 
         'kcontacts-git' 'kcalcore-git' 'kidentitymanagement-git' 'kldap-git' 'kmailtransport-git' 'kcalutils-git' 
         'kontactinterface-git' 'kholidays-git' 'ktnef-git' 'kimap-git' 'kmbox-git' 'akonadi-calendar-git' 
         'kde-syndication-git' 'gpgmepp-git' 'kalarmcal-git' 'kmime-git' 'kdepim-runtime-git'
         'kxmlrpcclient-git' 'kblog-git' 'kdepimlibs-git' 'akonadi-search-git')
makedepends=('boost' 'extra-cmake-modules' 'kdoctools' 'git' 'kdepim-runtime-git')
conflicts=('kdepim')
replaces=('kdepim')
source=("git://anongit.kde.org/kdepim.git")
sha256sums=('SKIP')

pkgver() {
  cd kdepim
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd ${srcdir}
  #sed -i 's|KF5::AkonadiPrivate|KF5::KF5AkonadiPrivate|' ${srcdir}/$_pkgname/akonadi_next/CMakeLists.txt

  mkdir build
  
  cd build 
  cmake ../${_pkgname} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_SKIP_RPATH=ON \
    -DLIB_INSTALL_DIR=lib \
    -DSYSCONF_INSTALL_DIR=/etc \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DKDEPIM_BUILD_MOBILE=FALSE
  make 
}

package() {
  cd ${srcdir}/build
  
  make DESTDIR=${pkgdir} install
}
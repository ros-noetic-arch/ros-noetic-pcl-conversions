# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Provides conversions from PCL data types and ROS message types."
url='https://wiki.ros.org/pcl_conversions'

pkgname='ros-noetic-pcl-conversions'
pkgver='1.7.5'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-noetic-catkin)
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-noetic-pcl-msgs
  ros-noetic-roscpp
  ros-noetic-sensor-msgs
  ros-noetic-std-msgs)
depends=(${ros_depends[@]}
  eigen
  pcl)

# Git version (e.g. for debugging)
# _tag=release/noetic/pcl_conversions/${pkgver}-${_pkgver_patch}
# _dir=${pkgname}
# source=("${_dir}"::"git+https://github.com/ros-gbp/perception_pcl-release.git"#tag=${_tag})
# sha256sums=('SKIP')

# Tarball version (faster download)
_commit="283496fd921a0b60e9ea1bba45561804226895e8"
_dir="perception_pcl-${_commit}/pcl_conversions"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-perception/perception_pcl/archive/${_commit}.tar.gz")
sha256sums=('4f3a6bf6d13a58e8e80e4fbc9b932e9bd9bc0c7b2b707014da68e29bcfb87472')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

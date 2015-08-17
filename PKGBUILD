# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Provides msgs, services and actions for STDR Simulator."
url='http://stdr-simulator-ros-pkg.github.io'

pkgname='ros-hydro-stdr-msgs'
pkgver='0.1.3'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('GPLv3')

ros_makedepends=(ros-hydro-message-generation
  ros-hydro-geometry-msgs
  ros-hydro-catkin
  ros-hydro-nav-msgs
  ros-hydro-actionlib-msgs
  ros-hydro-std-msgs)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-actionlib-msgs
  ros-hydro-message-runtime
  ros-hydro-geometry-msgs
  ros-hydro-nav-msgs
  ros-hydro-std-msgs)
depends=(${ros_depends[@]})

_tag=release/hydro/stdr_msgs/${pkgver}-${_pkgver_patch}
_dir=stdr_msgs
source=("${_dir}"::"git+https://github.com/stdr-simulator-ros-pkg/stdr_simulator-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

# Script generated with Bloom
pkgdesc="ROS - Low-level build system macros and infrastructure for ROS."
url='http://www.ros.org/wiki/catkin'

pkgname='ros-kinetic-catkin'
pkgver='0.7.11_2'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('cmake'
'python2'
'python2-catkin_pkg>0.2.9'
'python2-empy'
'python2-mock'
'python2-nose'
)

depends=('cmake'
'gmock'
'gtest'
'python2'
'python2-catkin_pkg>0.2.9'
'python2-empy'
'python2-nose'
)

conflicts=()
replaces=()

_dir=catkin
source=()
md5sums=()

prepare() {
    cp -R $startdir/catkin $srcdir/catkin
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=OFF \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}


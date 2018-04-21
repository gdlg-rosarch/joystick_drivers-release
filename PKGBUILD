# Script generated with Bloom
pkgdesc="ROS - ROS interface to the 3Dconnexion SpaceNavigator 6DOF joystick."
url='http://www.ros.org/wiki/spacenav_node'

pkgname='ros-lunar-spacenav-node'
pkgver='1.11.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('libspnav'
'libx11'
'ros-lunar-catkin'
'ros-lunar-geometry-msgs'
'ros-lunar-roscpp'
'ros-lunar-sensor-msgs'
)

depends=('libspnav'
'libx11'
'ros-lunar-geometry-msgs'
'ros-lunar-roscpp'
'ros-lunar-sensor-msgs'
'spacenavd'
)

conflicts=()
replaces=()

_dir=spacenav_node
source=()
md5sums=()

prepare() {
    cp -R $startdir/spacenav_node $srcdir/spacenav_node
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
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


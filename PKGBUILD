# Script generated with Bloom
pkgdesc="ROS - ROS driver for a generic Linux joystick. The joy package contains joy_node, a node that interfaces a generic Linux joystick to ROS. This node publishes a &quot;Joy&quot; message, which contains the current state of each one of the joystick's buttons and axes."
url='http://www.ros.org/wiki/joy'

pkgname='ros-kinetic-joy'
pkgver='1.11.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('linuxconsole'
'ros-kinetic-catkin'
'ros-kinetic-diagnostic-updater'
'ros-kinetic-rosbag'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
)

depends=('linuxconsole'
'ros-kinetic-diagnostic-updater'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
)

conflicts=()
replaces=()

_dir=joy
source=()
md5sums=()

prepare() {
    cp -R $startdir/joy $srcdir/joy
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
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
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


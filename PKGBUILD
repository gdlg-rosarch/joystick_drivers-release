# Script generated with Bloom
pkgdesc="ROS - The wiimote package allows ROS nodes to communicate with a Nintendo Wiimote and its related peripherals, including the Nunchuk, Motion Plus, and (experimentally) the Classic. The package implements a ROS node that uses Bluetooth to communicate with the Wiimote device, obtaining accelerometer and gyro data, the state of LEDs, the IR camera, rumble (vibrator), buttons, joystick, and battery state. The node additionally enables ROS nodes to control the Wiimote's LEDs and vibration for feedback to the human Wiimote operator. LEDs and vibration may be switched on and off, or made to operate according to a timed pattern."
url='http://www.ros.org/wiki/wiimote'

pkgname='ros-kinetic-wiimote'
pkgver='1.11.0_1'
pkgrel=1
arch=('any')
license=('GPL'
)

makedepends=('cwiid'
'python2-numpy'
'ros-kinetic-catkin'
'ros-kinetic-genmsg'
'ros-kinetic-geometry-msgs'
'ros-kinetic-roscpp'
'ros-kinetic-roslib'
'ros-kinetic-roslint'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
'ros-kinetic-std-msgs'
'ros-kinetic-std-srvs'
)

depends=('cwiid'
'python2-numpy'
'ros-kinetic-genmsg'
'ros-kinetic-geometry-msgs'
'ros-kinetic-roscpp'
'ros-kinetic-roslib'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
'ros-kinetic-std-msgs'
'ros-kinetic-std-srvs'
)

conflicts=()
replaces=()

_dir=wiimote
source=()
md5sums=()

prepare() {
    cp -R $startdir/wiimote $srcdir/wiimote
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


# Script generated with Bloom
pkgdesc="ROS - Playstation 3 SIXAXIS or DUAL SHOCK 3 joystick driver. Driver for the Sony PlayStation 3 SIXAXIS or DUAL SHOCK 3 joysticks. In its current state, this driver is not compatible with the use of other Bluetooth HID devices. The driver listens for a connection on the HID ports, starts the joystick streaming data, and passes the data to the Linux uinput device so that it shows up as a normal joystick."
url='http://www.ros.org/wiki/ps3joy'

pkgname='ros-kinetic-ps3joy'
pkgver='1.11.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('bluez'
'libusb-compat'
'linuxconsole'
'python2-pybluez'
'ros-kinetic-catkin'
'ros-kinetic-diagnostic-msgs'
'ros-kinetic-rosgraph'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
)

depends=('bluez'
'libusb-compat'
'linuxconsole'
'python2-pybluez'
'ros-kinetic-diagnostic-msgs'
'ros-kinetic-rosgraph'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
)

conflicts=()
replaces=()

_dir=ps3joy
source=()
md5sums=()

prepare() {
    cp -R $startdir/ps3joy $srcdir/ps3joy
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


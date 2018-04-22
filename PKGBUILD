# Script generated with Bloom
pkgdesc="ROS - The VRPN is a library and set of servers that interfaces with virtual-reality systems, such as VICON, OptiTrack, and others."
url='https://github.com/vrpn/vrpn/wiki'

pkgname='ros-kinetic-vrpn'
pkgver='7.33.1_2'
pkgrel=1
arch=('any')
license=('BSL1.0'
)

makedepends=('cmake'
)

depends=('ros-kinetic-catkin'
)

conflicts=()
replaces=()

_dir=vrpn
source=()
md5sums=()

prepare() {
    cp -R $startdir/vrpn $srcdir/vrpn
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


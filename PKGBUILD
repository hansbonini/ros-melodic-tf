# Script generated with import_catkin_packages.py.
# For more information: https://github.com/bchretien/arch-ros-stacks.
pkgdesc="ROS - tf is a package that lets the user keep track of multiple coordinate frames over time."
url='http://www.ros.org/wiki/tf'

pkgname='ros-melodic-tf'
pkgver='1.12.0'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(
	ros-melodic-angles
	ros-melodic-rostime
	ros-melodic-catkin
	ros-melodic-message-generation
	ros-melodic-std-msgs
	ros-melodic-tf2-ros
	ros-melodic-rosconsole
	ros-melodic-roscpp
	ros-melodic-message-filters
	ros-melodic-sensor-msgs
	ros-melodic-geometry-msgs
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
)

ros_depends=(
	ros-melodic-roswtf
	ros-melodic-message-runtime
	ros-melodic-std-msgs
	ros-melodic-tf2-ros
	ros-melodic-rosconsole
	ros-melodic-roscpp
	ros-melodic-message-filters
	ros-melodic-sensor-msgs
	ros-melodic-geometry-msgs
)

depends=(
	${ros_depends[@]}
	graphviz
)

_dir="geometry-release-release-melodic-tf-${pkgver}-${_pkgver_patch}"
source=("${pkgname}-${pkgver}-${_pkgver_patch}.tar.gz"::"https://github.com/ros-gbp/geometry-release/archive/release/melodic/tf/${pkgver}-${_pkgver_patch}.tar.gz")
sha256sums=('00d706fa94be4c4348556e8985dae8be407e76aae3f767e92dbd35e206f5ab03')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Fix boost_signals error
        cd ${_dir}
        rm -rf CMakeLists.txt
        wget https://raw.githubusercontent.com/ros/geometry/melodic-devel/tf/CMakeLists.txt

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Fix Python2/Python3 conflicts.
	/usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCMAKE_BUILD_TYPE=Release \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
		-DPYTHON_EXECUTABLE=/usr/bin/python3 \
		-DPYTHON_INCLUDE_DIR=/usr/include/python3.7m \
		-DPYTHON_LIBRARY=/usr/lib/libpython3.7m.so \
		-DPYTHON_BASENAME=.cpython-37m \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}

pkgdesc="ROS - urfdom headers file."
url='https://github.com/ros/metapackages'

pkgname='urdfdom-headers'
pkgver='1.0.4'
_pkgver_patch=0
arch=('any')
pkgrel=2
license=('BSD')

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
)

depends=(
)

_dir="urdfdom_headers-master"
source=("${pkgname}-${pkgver}.zip"::"https://github.com/ros/urdfdom_headers/archive/master.zip")
sha256sums=('ad31685d6527fe6568a84bd8e513fdcd42146c790eb53c7bb951b9ad7c6b3cd8')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Build the project.
    
    cmake ${srcdir}/${_dir} \
    	-DCMAKE_BUILD_TYPE=Release \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
		-DPYTHON_BASENAME=.cpython-37

	make

}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}

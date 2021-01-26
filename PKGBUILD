pkgname=capi
pkgver=1.0
pkgrel=1
arch=(any)

makedepends=(git)
source=(
	git+https://github.com/bulletphysics/bullet3
	git+https://github.com/mrjuan1/bulletcapi#branch=feature/shared
)
md5sums=(SKIP SKIP)

prepare() {
	cd bulletcapi
	ln -sfv ../bullet3
}

build() {
	cd bulletcapi/capi
	make
}

package() {
	cd bulletcapi/capi
	mkdir -pv $pkgdir/usr/include
	cp -v capi.h $pkgdir/usr/include
	cd lib
	strip -s libbullet.so libcapi.so
	mkdir -pv $pkgdir/usr/lib
	cp -v libbullet.so libcapi.so $pkgdir/usr/lib
}

_pkgname=dmenu
pkgname=dmenu-gatonegro-git
pkgver=5.2.r2.83b0717
pkgrel=1
pkgdesc="Gatonegro's custom build of dmenu."
url="https://github.com/adolfgatonegro/dmenu"
arch=(x86_64)
license=(MIT)
makedepends=(git)
provides=($_pkgname)
conflicts=($_pkgname)
source=(git+$url)
sha256sums=('SKIP')

pkgver() {
	cd "$_pkgname"
	echo "$(awk '/^VERSION =/ {print $3}' config.mk)".r"$(git rev-list --count HEAD)"."$(git rev-parse --short HEAD)"
}

build() {
	cd "$_pkgname"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd "$_pkgname"
	make PREFIX=/usr DESTDIR="$pkgdir" install
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

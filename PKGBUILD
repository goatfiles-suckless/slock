# Maintainer: Antoine Stevan
pkgname=slock-a2ns-git
pkgver=5.0.r589.8c0f76a
pkgrel=1
epoch=
pkgdesc="A heavily patched build of slock."
arch=(x86_64)
url="https://github.com/a2n-s/slock.git"
license=('GNU')
groups=()
depends=()
makedepends=(git)
checkdepends=()
optdepends=()
provides=(slock)
conflicts=(slock)
replaces=()
backup=()
options=()
install=
changelog=
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
	cd "${_pkgname}"
  printf "5.0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd slock
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd slock
    mkdir -p ${pkgdir}/opt/${pkgname}
    cp -rf * ${pkgdir}/opt/${pkgname}
    make PREFIX=/usr DESTDIR="${pkgdir}" install
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}

_pkgname="swayfire"
repo="https://github.com/Javyre/swayfire"
url="$repo"
pkgname="${_pkgname}-git"
pkgdesc="Sway/I3 inspired tiling window manager for Wayfire."
builddir="${srcdir}/${_pkgname}"
pkgver="_git"
pkgrel=0
provides="swayfire=_git"
options="!check"
arch="all"
license="GPL"
makedepends="git
	     meson
	     wayfire-git-dev"

prepare() {
    default_prepare
    cd "${srcdir}"
    git clone --depth=1 "${repo}" || return 1
}

build() {
    cd "${builddir}"
    meson setup --prefix /usr build
    meson compile -C build
}

package() {
    cd "${builddir}"
    DESTDIR="$pkgdir/" meson install -C build
}

#Maintainer: Gerrit G. <gerrit at grosskopfgames dot de>
pkgname=unl0kr
pkgver=2.0.2
pkgdesc="On-screen Keyboard for FDE"
pkgrel=1
arch=(x86_64)
url="https://github.com/Grosskopf/arch_unl0kr"
license=('GPL3')
depends=(device-mapper cryptsetup)
makedepends=(meson)
_commit="2e5707cbd5d8d9ab1b382f663e57804e1fb063ef"
source=(
    git+https://gitlab.com/cherrypicker/unl0kr.git#commit=${_commit}
    unl0kr-hooks
    unl0kr-install
    shift_logo.patch
)
backup=(etc/unl0kr.conf)
build() {
    cd unl0kr
    git am ../shift_logo.patch
    git submodule init
    git submodule update
    cd ..
    arch-meson "$pkgname" _build
    meson compile -C _build
}
package() {
    DESTDIR="$pkgdir" meson install --no-rebuild -C _build
    install -Dm644 ${srcdir}/unl0kr-hooks ${pkgdir}/usr/lib/initcpio/hooks/unl0kr
    install -Dm644 ${srcdir}/unl0kr-install ${pkgdir}/usr/lib/initcpio/install/unl0kr
}
md5sums=('SKIP'
         'bfb3b7489f6ad4eff1a934ee469dc101'
         '79bb712c36c48179ab3eaab9d9d902db'
         'd70e33266d0b44295e27b9e95a7cf45d')

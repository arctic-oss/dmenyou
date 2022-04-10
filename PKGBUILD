# Maintainer: Anil Beesetti

pkgname=dmenyou
pkgver=5.1
pkgrel=1
patchver=5.0
pkgdesc="Fork of dmenu"
url="https://www.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
license=('GPL')
depends=('libxinerama' 'libxft')
conflicts=(dmenu)
source=("https://dl.suckless.org/tools/dmenu-$pkgver.tar.gz"
        "https://tools.suckless.org/dmenu/patches/line-height/dmenu-lineheight-$patchver.diff")
sha256sums=('1f4d709ebba37eb7326eba0e665e0f13be4fa24ee35c95b0d79c30f14a348fd5'
            '7e8584ba30da1a5dcfa9c357298ecf8eb173c6396df21d8bc14cdaef937794b6')

build() {
    cp $srcdir/dmenu-lineheight-$patchver.diff $srcdir/dmenu-$pkgver/
    cd $srcdir/dmenu-$pkgver
    patch -p1 < dmenu-lineheight-$patchver.diff
    make
}

package() {
    cd $srcdir/dmenu-$pkgver
    make DESTDIR="$pkgdir" PREFIX=/usr install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/dmenu/LICENSE"
}

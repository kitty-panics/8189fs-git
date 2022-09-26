# Maintainer: swiftgeek
# Contributor: Kitty Panics

pkgname=8189fs-git
_pkgname=rtl8189ES_linux
pkgver=5.2.0
pkgrel=1
pkgdesc="Kernel module for Realtek RTL8189FTV SDIO wireless devices."
arch=('armv7h')
url="https://github.com/jwrdegoede/rtl8189ES_linux/tree/rtl8189fs"
license=('GPL')
depends=('linux')
source=("git+https://github.com/jwrdegoede/$_pkgname.git#branch=rtl8189fs")
sha256sums=('SKIP')
install=depmod.install

_KVER="$(pacman -Q | grep linux-armv7 | head -1 | cut -d' ' -f2)"
_extramodules="$(basename $(readlink -f /usr/lib/modules/$_KVER-ARCH/extramodules/))"

pkgver() {
    echo "$_KVER" | cut -d'-' -f1
}

build() {
    cd "$_pkgname"
    make ARCH=arm KSRC="/usr/lib/modules/$_KVER-ARCH/build/"
    gzip -9 8189fs.ko
}

package() {
    install -d "$pkgdir/usr/lib/modules/${_extramodules}/"
    install -m644 "$srcdir/$_pkgname/8189fs.ko.gz" \
        "$pkgdir/usr/lib/modules/${_extramodules}/8189fs.ko.gz"
}

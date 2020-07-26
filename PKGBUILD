# Maintainer: liberodark

pkgname=lwks
pkgver=2020.1
pkgbuild=r122068
pkgrel=1
pkgdesc="Lightworks version 2020"
arch=('x86_64')
options=('!strip')
url="http://www.lwks.com/"
license=('custom')
depends=('cairo' 'gdk-pixbuf2' 'glib2' 'libjpeg-turbo' 'pango' 'curl' 'gtk3' 'openssl' 'libgl' 'libtiff' 'libutil-linux' 'ffmpeg' 'glu' 'libedit' 'nvidia-cg-toolkit' 'openssl-1.0')
optdepends=('nvidia-utils: only for nVidia users' 'libc++: only for BlackMagic RAW support (BRAW)' 'libc++abi: only for BlackMagic RAW support (BRAW)')
conflicts=('lightworks' 'lwks' 'lwks-beta')
source=(
    "https://cdn.lwks.com/releases/lightworks-$pkgver-$pkgbuild-amd64.deb"
    )

sha256sums=(
    '23ed5b617628ac278cc5b2f0f799f53368e3b00203c55ddc65e25be3e9f14fbf'
    )

package() {
    msg2 "Extracting data.tar.xz"
    bsdtar -zxf data.tar.xz -C "$pkgdir"

    msg2 "Moving udev folder from /lib to /usr/lib"
    mv "$pkgdir"/lib/udev "$pkgdir"/usr/lib
    rmdir "$pkgdir"/lib

    msg2 "Copying copyright file and creating a license dir"
    install -Dm644 "$pkgdir"/usr/share/doc/lightworks/copyright \
    "$pkgdir"/usr/share/licenses/lightworks/copyright
    ln -sr "$pkgdir"/usr/share/licenses/lightworks "$pkgdir"/usr/share/licenses/$pkgname

    msg2 "Changing some needed permissions"
    chmod a+rw "$pkgdir"/usr/share/lightworks/Preferences
    chmod a+rw "$pkgdir"/usr/share/lightworks/"Audio Mixes"
}

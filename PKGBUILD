# Maintainer: liberodark

pkgname=lightworks
pkgver=2020.1
pkgrel=122068
pkgdesc="Lightworks version 2020"
arch=('x86_64')
options=('!strip')
url="http://www.lwks.com/"
license=('custom')
depends=('cairo' 'gdk-pixbuf2' 'glib2' 'libjpeg-turbo' 'pango' 'curl' 'gtk3' 'openssl' 'libgl' 'libtiff' 'libutil-linux' 'ffmpeg' 'glu' 'libedit' 'nvidia-cg-toolkit' 'openssl-1.0')
optdepends=('nvidia-utils: only for nVidia users' 'libc++: only for BlackMagic RAW support (BRAW)' 'libc++abi: only for BlackMagic RAW support (BRAW)')
conflicts=('lightworks' 'lwks' 'lwks-beta')
source=(
    "https://cdn.lwks.com/releases/$pkgname-$pkgver-r$pkgrel-amd64.deb"
    )

sha256sums=(
    '23ed5b617628ac278cc5b2f0f799f53368e3b00203c55ddc65e25be3e9f14fbf'
    )

package() {
    msg2 "Extracting data.tar.xz"
    tar -zxf data.tar.xz -C "$pkgdir"

    msg2 "Moving udev folder from /lib to /usr/lib"
    mv "$pkgdir"/lib/udev "$pkgdir"/usr/lib
    rmdir "$pkgdir"/lib

    msg2 "Copying copyright file and creating a license dir"
    install -Dm644 "$pkgdir"/usr/share/doc/lightworks/copyright \
    "$pkgdir"/usr/share/licenses/lightworks/copyright

    msg2 "Changing some needed permissions"
    chmod a+rw "$pkgdir"/usr/share/lightworks/Preferences
    chmod a+rw "$pkgdir"/usr/share/lightworks/"Audio Mixes"
}

# Maintainer: liberodark

pkgname=lightworks
pkgver=2020.1.1
pkgbuild=r124942
pkgrel=1
pkgdesc="Lightworks version 2020"
arch=('x86_64')
options=('!strip')
url="http://www.lwks.com/"
license=('custom')
depends=('cairo' 'gdk-pixbuf2' 'glib2' 'libjpeg-turbo' 'pango' 'curl' 'gtk3' 'openssl' 'libgl' 'libtiff' 'libutil-linux' 'ffmpeg' 'glu' 'libedit' 'nvidia-cg-toolkit' 'openssl-1.0')
optdepends=('nvidia-utils: only for nVidia users' 'libc++: only for BlackMagic RAW support (BRAW)' 'libc++abi: only for BlackMagic RAW support (BRAW)')
conflicts=('lightworks' 'lwks' 'lwks-beta')
source=("https://cdn.lwks.com/releases/$pkgver/lightworks_2020.1.1_r124942.deb")

sha256sums=('e4da98e4439b45220f37ec748d829e72bc8580f6efa1384c882e4fbdb69a7f81')

package() {
    msg2 "Extracting data.tar.xz"
    tar -xvf data.tar.xz -C "$pkgdir"

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

# Maintainer : Martin Wimpress <code@flexion.org>
# Contributor: Giovanni "Talorno" Ricciardi <kar98k.sniper@gmail.com>
# Contributor: Xpander <xpander0@gmail.com>

pkgname=mate-image-viewer
pkgver=1.6.2
pkgrel=1
pkgdesc="An image viewing and cataloging program for MATE"
url="http://mate-desktop.org"
arch=('i686' 'x86_64')
license=('GPL')
depends=('dbus-glib' 'desktop-file-utils' 'gtk2' 'exempi' 'lcms' 'libexif'
         'libjpeg-turbo' 'mate-desktop' 'mate-icon-theme' 'pygtk' 'python2'
         'python2-gobject2' 'startup-notification' 'zlib')
makedepends=('mate-common' 'mate-doc-utils' 'perl-xml-parser')
options=('!emptydirs')
groups=('mate-extra')
source=("http://pub.mate-desktop.org/releases/1.6/${pkgname}-${pkgver}.tar.xz"
        "https://github.com/mate-desktop/eom/commit/e62ed087493c8a529d4eeab46c7d68a2047ac81a.diff")
sha1sums=('37e638790329350bb772a40549741f89ed43952c'
          'a2f0810a48d81023e9bae29d80b682ae0fe9faac')
install=${pkgname}.install

prepare() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    #Use GETTEXT_PACKAGE instead of PACKAGE
    patch -Np1 -i "${srcdir}/e62ed087493c8a529d4eeab46c7d68a2047ac81a.diff"
}

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    PYTHON=/usr/bin/python2 ./configure \
        --prefix=/usr \
        --localstatedir=/var \
        --disable-scrollkeeper
    make
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
}

# $Id$
# Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=libsoup-lite
_realname=libsoup
pkgver=2.42.2
pkgrel=2
pkgdesc="GNOME HTTP Library"
arch=('i686' 'x86_64')
license=('LGPL')
url="http://www.gnome.org"
depends=('glib2' 'libxml2' 'gnutls' 'sqlite')
makedepends=('intltool' 'gobject-introspection' 'python2')
provides=('libsoup' 'libsoup-gnome')
conflicts=('libsoup-gnome' 'libsoup')
replaces=('libsoup-gnome' 'libsoup')
options=('!libtool' '!emptydirs')
source=(http://ftp.gnome.org/pub/gnome/sources/$_realname/${pkgver%.*}/$_realname-$pkgver.tar.xz)
sha256sums=('1f4f9cc55ba483dc8defea0c3f97cc507dc48384c5529179e29c1e6d05630dbf')

build() {
  cd $_realname-$pkgver

  # Python3 has UnicodeDecodeErrors
  sed -i -e '1s/python$/&2/' libsoup/tld-parser.py

  ./configure --prefix=/usr \
      --sysconfdir=/etc \
      --localstatedir=/var \
      --disable-static \
      --disable-tls-check \
      --without-gnome
  make
}

package() {
  cd $_realname-$pkgver
  make DESTDIR="$pkgdir" install
}

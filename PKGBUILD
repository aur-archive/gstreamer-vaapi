# Maintainer:	Jesse Jaara		<gmail.com: jesse.jaara>
# Contributor:	Alessandro Pazzaglia	<gmail.com: jackdroido>

pkgname=gstreamer-vaapi
pkgver=0.5.2
pkgrel=1
pkgdesc="A collection of VA-API based plugins for GStreamer"
url="http://gitorious.org/vaapi/gstreamer-vaapi"
arch=('i686' 'x86_64')
license=('GPL2')
makedepends=('libva-wayland')
depends=('gstreamer0.10-base' 'gstreamer0.10-bad' 'libva')
makedepends=('gtk-doc')
optdepends=('xvba-video: for ATI chipsets'
            'libva-wayland: Wayland support'
	    'libva-vdpau-driver: for nVidia chipsets'
	    'libva-intel-driver: For Intel chipsets')
source=("http://www.freedesktop.org/software/vaapi/releases/${pkgname}/${pkgname}-${pkgver}.tar.bz2")
options=('!libtool')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  LIBS=-ldl ./configure  --prefix=/usr --disable-static
  sed 's|^LIBS =|LIBS = -lgstbasevideo-0.10 |'  -i tests/Makefile
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  make DESTDIR="${pkgdir}/" install
}

md5sums=('849825cad1def77ab5199a2b9b1b7bdb')

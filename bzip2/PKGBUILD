# Maintainer: cpasjuste <cpasjuste@gmail.com>

pkgname=ps4-openorbis-bzip2
pkgver=1.0.6
pkgrel=3
pkgdesc="A high-quality data compression program"
arch=('any')
license=('custom')
url="http://www.bzip.org"
options=(!strip !debug libtool staticlibs)
source=(http://http.debian.net/debian/pool/main/b/bzip2/bzip2_$pkgver.orig.tar.bz2)
sha256sums=('d70a9ccd8bdf47e302d96c69fecd54925f45d9c7b966bb4ef5f56b770960afa7')
makedepends=('ps4-openorbis-pkg-config' 'ps4-openorbis-vars')
groups=(
  'pacbrew' 'pacbrew-ps4' 'pacbrew-ps4-portlibs'
  'ps4-openorbis-portlibs' # for backward compatibility
)

build() {
  source /opt/pacbrew/ps4/openorbis/ps4vars.sh

  make -C "$srcdir/bzip2-$pkgver" \
    CC=${CC} \
    AR=${AR} \
    RANLIB=${RANLIB} \
    CPPFLAGS="${CPPFLAGS}" \
    CFLAGS="-D_FILE_OFFSET_BITS=64 -Winline ${CFLAGS}" libbz2.a
}

package() {
  source /opt/pacbrew/ps4/openorbis/ps4vars.sh

  install -Dm 644 "$srcdir/bzip2-$pkgver"/bzlib.h -t "${pkgdir}/${OPENORBIS}/usr/include/"
  install -Dm 644 "$srcdir/bzip2-$pkgver"/libbz2.a -t "${pkgdir}/${OPENORBIS}/usr/lib"
}

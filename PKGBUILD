# Maintainer: Alucryd <alucryd at gmail dot com>

pkgname=ffmpegsource
pkgver=2.17
pkgrel=8
pkgdesc="A libav/ffmpeg based source library and Avisynth plugin for easy frame accurate access"
arch=('x86_64' 'i686')
url="http://code.google.com/p/ffmpegsource/"
license=('MIT')
depends=('ffmpeg')
conflicts=('ffmpegsource2-svn')
options=('!libtool')
source=("http://ffmpegsource.googlecode.com/files/ffms-${pkgver}-src.tar.bz2")
sha1sums=('3bbd5b5f13dce4374efdd3e2bf048436295e6771')

build() {
  cd "${srcdir}"/ffms-$pkgver-src
  sed -i 's|avcodec_init|avcodec_register_all|g' configure.in
  sed -i 's|AM_CONFIG_HEADER|AC_CONFIG_HEADERS|g' configure.in
  sed -i 's|CodecID|AVCodecID|g' src/core/matroskaparser.{h,c}
  mv configure.in configure.ac
  ./autogen.sh --prefix=/usr --enable-shared --disable-static
  make
}

package() {
  cd "${srcdir}"/ffms-${pkgver}-src
  make DESTDIR="${pkgdir}" install
  install -dm 755 "${pkgdir}"/usr/share/licenses/ffmpegsource
  install -m 644 COPYING "${pkgdir}"/usr/share/licenses/ffmpegsource/license.txt
}

# vim: ts=2 sw=2 et:

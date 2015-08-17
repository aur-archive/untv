# Maintainer: Eric Engestrom <aur [at] engestrom [dot] ch>

pkgname=untv
pkgver=0.8.2
pkgrel=1
pkgdesc="DRM-Free Media Center Platform for Home Theater Computers"
arch=('x86_64')
url="http://untvapp.com"
license=('GPL3')
depends=('gtk2' 'nss' 'gconf' 'alsa-lib')
provides=('UnTV')
options=('!strip')

[ "$CARCH" = "i686" ]   && _platform=linux32
[ "$CARCH" = "x86_64" ] && _platform=linux64

source=("https://github.com/untv/untv/releases/download/v${pkgver}/untv-${pkgver}-${_platform}.zip"
        "UnTV.desktop"
        "UnTV.png")
md5sums=('platform-dependent'
         'f652353a1675031701cea0146098ea17'
         '643fe5bb4b003e4f1ca47b81ac9c8f04')

[ "$CARCH" = "i686" ]   && md5sums[0]='00000000000000000000000000000000'
[ "$CARCH" = "x86_64" ] && md5sums[0]='6ff976fe7af9155fa1c6eda672e2ce74'

package() {
  cd "${srcdir}/${pkgname}-${pkgver}-${_platform}"

  # Program
  local _DEST="/usr/share/${pkgname}"
  msg2 "Installing program to ${_DEST}"
  install -dm755 "${pkgdir}${_DEST}"
  install -m755 "UnTV" "${pkgdir}${_DEST}"
  install -m755 "nw.pak" "${pkgdir}${_DEST}"
  install -m755 "libffmpegsumo.so" "${pkgdir}${_DEST}"

  # Link to program
  msg2 "Symlink /usr/bin/${provides[0]} -> ${_DEST}/UnTV"
  mkdir -p "${pkgdir}/usr/bin"
  ln -s "${_DEST}/UnTV" "${pkgdir}/usr/bin/${provides[0]}"

  # Desktop icon
  install -Dm644 "${srcdir}/UnTV.desktop" "${pkgdir}/usr/share/applications/UnTV.desktop"
  install -Dm644 "${srcdir}/UnTV.png" "${pkgdir}/usr/share/pixmaps/UnTV.png"
}

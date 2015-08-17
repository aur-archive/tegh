# Maintainer: Rob Gilson <d1plo1d@d1plo1d.com>
pkgname=tegh
_gitname=tegh
pkgver=0.3.1
pkgrel=1
pkgdesc="A command line client to remotely monitor and control 3D printers running Prontserve."
url="https://github.com/D1plo1d/tegh"
arch=('any')
license=('MIT')
depends=('nodejs' 'coffee-script')
optdepends=()
makedepends=()
conflicts=()
replaces=()
backup=()
source=("git+https://github.com/D1plo1d/tegh.git#tag=0.3.0")
sha256sums=('SKIP')

pkgver() {
  cd $_gitname
  git describe --always | sed 's|-|.|g'
}

build() {
  cd "${srcdir}/${_gitname}"
  npm install
}

package() {
  install -dm755 ${pkgdir}/usr/{bin,share/tegh/{src,node_modules}}
  cp -R "${srcdir}/${_gitname}/src" "${pkgdir}/usr/share/tegh/"
  cp -R "${srcdir}/${_gitname}/node_modules" "$pkgdir/usr/share/tegh/"
  install -Dm644 "${srcdir}/${_gitname}/package.json" "$pkgdir/usr/share/tegh/package.json"

  echo -e "#!/bin/sh\n/usr/bin/env coffee /usr/share/tegh/src/tegh.coffee\n" > "${pkgdir}/usr/bin/tegh"
  chmod 755 "${pkgdir}/usr/bin/tegh"
}
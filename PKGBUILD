# Maintainer: Willy Goiffon <w.goiffon@gmail.com>
pkgname=ptii-dumb
pkgver=0.1.0
pkgrel=1
pkgdesc="CLI-like environment to interact with ii (irc it) -- dumb version"
url="https://gitorious.org/stii/ptii"
arch=('x86_64' 'i686')
license=('WTFPL')
depends=('ii')
optdepends=('multitail')
makedepends=('git')
conflicts=()
replaces=()
backup=()
install=
source=()
md5sums=()

_gitroot=git://gitorious.org/stii/ptii.git
_gitbranch=core

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "${pkgname}-${pkgver}" ]]; then
    cd "${pkgname}-${pkgver}" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "${pkgname}-${pkgver}" -b "$_gitbranch"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/${pkgname}-${pkgver}-build"
  git clone "${srcdir}/${pkgname}-${pkgver}" "$srcdir/${pkgname}-${pkgver}-build"
  cd "${srcdir}/${pkgname}-${pkgver}-build"
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
  echo "hey pssst... take a look at the README ;)"
}

# vim:set ts=2 sw=2 et:

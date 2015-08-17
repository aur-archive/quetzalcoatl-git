# Maintainer: Peter Richard Lewis <plewis@aur.archlinux.org>
# Contributor: linopolus <linopolus@xssn.at>
pkgname=quetzalcoatl-git
pkgver=20111223
pkgrel=1
pkgdesc="Quetzalcoatl is a KDE4 music player client for the MPD music server."
arch=('any')
url="http://www.vcn.bc.ca/~dugan/quetzalcoatl.html"
license=('GPL3')
groups=()
depends=('python-mpd-git' 'kdebindings-python')
makedepends=('git')
provides=('quetzalcoatl')
conflicts=('quetzalcoatl')
conflicts=()
replaces=()
backup=()
options=()
install=
source=()
noextract=()
md5sums=() #generate with 'makepkg -g'

_gitroot="https://github.com/duganchen/quetzalcoatl.git"
_gitname=quetzalcoatl

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  # Nothing to build, it's just one python file!

  # Tell it to use python2
  sed -i 's/\/usr\/bin\/python$/\/usr\/bin\/python2/' quetzalcoatl.py

  mkdir -p $pkgdir/usr/bin
  cp quetzalcoatl.py $pkgdir/usr/bin/quetzalcoatl
}

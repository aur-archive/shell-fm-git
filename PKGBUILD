# Contributor: Geoffroy Carrier <geoffroy.carrier@koon.fr>
pkgname=shell-fm-git
pkgver=20121211
pkgrel=1
pkgdesc="A console based player for the streams provided by Last.fm"
arch=('i686' 'x86_64')
url="http://github.com/jkramer/shell-fm"
# url="http://github.com/AndydeCleyre/shell-fm"
license=('GPL')
depends=('libmad' 'libao' 'taglib')
makedepends=('git')
provides=('shell-fm')
conflicts=('shell-fm')

_gitroot="git://github.com/jkramer/shell-fm.git"
# _gitroot="git://github.com/AndydeCleyre/shell-fm.git"
_gitname="shell-fm"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d "$srcdir/$_gitname" ] ; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  cp -r "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  make
  make DESTDIR="${pkgdir}" MANDIR="/usr/share/man" install
}

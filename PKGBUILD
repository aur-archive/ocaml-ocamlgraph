# Maintainer: Serge Zirukin <ftrvxmtrx@gmail.com>
# Contributor: Sergei Lebedev <superbobry@gmail.com>
# Contributor: Thomas S Hatch <thatch45 at gmail dot com>
# Contributor: Paolo Herms
# Contributor: Magnus Therning <magnus@therning.org>
# Contributor: Jose Neder <jlneder(at)gmail(dot)com>

pkgname=ocaml-ocamlgraph
pkgver=1.8.2
pkgrel=2
pkgdesc="Graph library for OCaml"
url="http://ocamlgraph.lri.fr"
source=("http://ocamlgraph.lri.fr/download/ocamlgraph-$pkgver.tar.gz")
md5sums=('efa4394bc4651c90de443ff61c7477e6')
options=('!strip' '!makeflags')
depends=('ocaml')
makedepends=('ocaml-findlib' 'lablgtk2')
arch=('i686' 'x86_64')
license=('LGPL')

build() {
  cd "$srcdir/ocamlgraph-$pkgver"
  ./configure --prefix=/usr
  make all viewer doc
}

package() {
  cd "$srcdir/ocamlgraph-$pkgver"
  export OCAMLFIND_DESTDIR=$pkgdir$(ocamlfind printconf destdir)
  mkdir -p $OCAMLFIND_DESTDIR
  make DESTDIR=$pkgdir install-findlib
  install -d -m 0755 "${pkgdir}/usr/share/doc/$pkgname"
  install -t "${pkgdir}/usr/share/doc/$pkgname/" doc/*
  install -Dm 755 dgraph/dgraph.opt "${pkgdir}/usr/bin/graph-viewer"
  install -Dm 755 editor/editor.opt "${pkgdir}/usr/bin/graph-editor"
}

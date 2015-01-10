# Maintainer: Mahmud Ridwan <m[at]hjr265[dot]me>
pkgname=arturia
pkgver=20150110
pkgrel=1
pkgdesc=Saber
url="https://arturia.io"
arch=('x86_64')
license=('Proprietary')
makedepends=('go')
backup=(
  'etc/arturia.tml'
)
source=(
  'arturia@.service'
)
md5sums=(
  'dff789834ecb6c51c3500804bfde7324'
)

build() {
  mkdir -p "$srcdir"/src/git.hjr265.me/arturia
  git clone https://git.hjr265.me/arturia/arturia.git "$srcdir"/src/git.hjr265.me/arturia/arturia
  GOPATH="$srcdir" go get git.hjr265.me/arturia/arturia/...
}

package() {
  install -m755 -d "$pkgdir/usr/bin"
  install -m755 "$srcdir/bin/arturiad" "$pkgdir/usr/bin/arturiad"
  install -m755 "$srcdir/bin/arturia-cubed" "$pkgdir/usr/bin/arturia-cubed"
  install -m755 -d "$pkgdir/usr/lib/systemd/system"
  install -m644 arturia@.service "$pkgdir/usr/lib/systemd/system"
  install -m755 -d "$pkgdir/etc"
  install -m644 "$srcdir/src/git.hjr265.me/arturia/arturia/cmd/arturiad/config-sample.tml" "$pkgdir/etc/arturia.tml"
}

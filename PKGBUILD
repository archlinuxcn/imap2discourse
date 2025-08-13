# Maintainer: lilydjwg <lilydjwg@gmail.com>

_pkgname=imap2discourse
pkgname=$_pkgname-git
pkgver=r2.f009ab8
pkgrel=4
pkgdesc="Forward mails from IMAP to Discourse"
arch=('any')
url="https://github.com/archlinuxcn/imap2discourse"
license=(GPL-3.0-or-later)
depends=('python' 'python-aioimaplib' 'python-httpx')
makedepends=('git')
source=("git+${url}.git")
backup=(etc/$_pkgname/config.toml)
sha256sums=('SKIP')

pkgver() {
  cd $_pkgname
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  true
}

package() {
  cd $_pkgname
  install -Dm755 imap2discourse -t "$pkgdir/usr/bin/"
  mkdir "$pkgdir/etc"
  mkdir -m700 "$pkgdir/etc/$_pkgname"
  install -m600 config.toml.example "$pkgdir/etc/$_pkgname/config.toml"
  install -Dm644 $_pkgname.service "$pkgdir/usr/lib/systemd/system/$_pkgname.service"
}

# vim:set ts=2 sw=2 et:

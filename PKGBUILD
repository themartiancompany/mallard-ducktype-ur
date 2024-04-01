# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgname=mallard-ducktype
pkgver=1.0.2
pkgrel=9
pkgdesc="Parser for the lightweight Ducktype syntax for Mallard"
url="http://projectmallard.org"
arch=(any)
license=(MIT)
depends=(python)
makedepends=(
  git
  python-build
  python-installer
  python-setuptools
  python-wheel)
_commit=5d0fe2c23571f4463b77afa1ffd2c2bf5e6316f4  # tags/1.0.2^0
source=("git+https://github.com/projectmallard/mallard-ducktype#commit=$_commit")
sha256sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/-/+/g'
}

build() {
  cd $pkgname
  python -m build --wheel --no-isolation
}

package() {
  cd $pkgname
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dt "$pkgdir/usr/share/licenses/$pkgname" -m644 COPYING
}

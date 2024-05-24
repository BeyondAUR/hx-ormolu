# Maintainer: Evan Greenup <_>

_name=ormolu
pkgname=hx-ormolu
pkgver=0.7.4.0
pkgrel=1
pkgdesc="A formatter for Haskell source code"
url="https://github.com/tweag/ormolu"
license=("BSD-3-Clause")
arch=('x86_64')
provides=('ormolu' 'haskell-ormolu')
conflicts=('ormolu' 'haskell-ormolu')
replaces=('ormolu' 'haskell-ormolu')
depends=()
makedepends=('stack')
source=("${_name}-${pkgver}.tar.gz::https://github.com/tweag/${_name}/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('7d30dea0adf6511a7a872fadb06cf037bc5ef118450b1618e6d1900785439444')

_stack_resolver=nightly-2024-05-24

build() {
  cd "$srcdir/$_name-$pkgver"

  stack --resolver=${_stack_resolver} build ormolu:exe:ormolu
}

check() {
  cd "$srcdir/$_name-$pkgver"

  stack --resolver=${_stack_resolver} test ormolu:test:tests
}

package() {
  cd "$srcdir/$_name-$pkgver"
  mkdir -m755 -p "${pkgdir}/usr/bin/"
  install -m755 "$(stack --resolver=${_stack_resolver} path --local-install-root)/bin/ormolu" "${pkgdir}/usr/bin/ormolu"
  install -D -m644 LICENSE.md -t "$pkgdir"/usr/share/licenses/$pkgname/
}

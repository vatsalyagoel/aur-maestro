pkgname=maestro
pkgver=2.9.0
pkgrel=1
pkgdesc='Mobile UI testing framework'
arch=('any')
url='https://maestro.dev'
license=('Apache-2.0')
depends=('bash' 'java-runtime-headless>=17')
makedepends=('java-environment>=17')
conflicts=('maestro-bin' 'maestro-dev')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/mobile-dev-inc/maestro/archive/refs/tags/cli-${pkgver}.tar.gz")
sha256sums=('483a723cf4fa7d88184f540f1a25fdb8c307dc3cc34388a9067cbf82e64c7734')

build() {
  cd "Maestro-cli-${pkgver}"
  GRADLE_USER_HOME="$srcdir/.gradle" ./gradlew --no-daemon :maestro-cli:installDist
}

package() {
  cd "Maestro-cli-${pkgver}"
  install -d "$pkgdir/opt/maestro" "$pkgdir/usr/bin"
  cp -a maestro-cli/build/install/maestro/. "$pkgdir/opt/maestro/"
  ln -s /opt/maestro/bin/maestro "$pkgdir/usr/bin/maestro"
}

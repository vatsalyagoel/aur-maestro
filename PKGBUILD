pkgname=maestro
pkgver=2.11.0
pkgrel=1
pkgdesc='Mobile UI testing framework'
arch=('any')
url='https://maestro.dev'
license=('Apache-2.0')
depends=('bash' 'java-runtime-headless>=17')
makedepends=('java-environment>=17')
conflicts=('maestro-bin' 'maestro-dev')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/mobile-dev-inc/maestro/archive/refs/tags/cli-${pkgver}.tar.gz")
sha256sums=('f259c84845b722b1beeeeba21978803359880c4dab1221c44dffd56d8406e725')

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

pkgname=teledatics-cli-app-git
pkgver=1.0.0
pkgrel=1
pkgdesc="Teledatics CLI App for the TD-XPAH development board (Host Mode)"
arch=('any')
url=""
license=('GPL2')
depends=('base')
source=("${srcdir}/${pkgname}::git+https://github.com/teledatics/nrc7292_sw_pkg")
sha256sums=('SKIP')

# Remove this entire section after https://github.com/teledatics/nrc7292_sw_pkg/pull/1 is merged
prepare() {
    sed -i -e '30s/$/ lib$(TARGET).a/' "${srcdir}/${pkgname}/package/host/src/cli_app/Makefile"
}

build() {
    cd "${srcdir}/${pkgname}/package/host/src/cli_app"
    make
}

package() {
    install -Dm755 "${srcdir}/${pkgname}/package/host/src/cli_app/cli_app" "${pkgdir}/usr/bin/teledatics-cli-app"
}
pkgname=m4
pkgver=1.4.20
pkgrel=1
pkgdesc="The GNU macro processor"
arch=('x86_64')
url="https://www.gnu.org/software/m4/"
license=('GPL3')
groups=('base-devel')
depends=('glibc')
options=('!lto')
source=(https://ftp.gnu.org/gnu/${pkgname}/${pkgname}-${pkgver}.tar.xz)
sha256sums=(e236ea3a1ccf5f6c270b1c4bb60726f371fa49459a8eaaebc90b216b328daf2b)

prepare() {
    cd ${pkgname}-${pkgver}

    sed 's/\[\[__nodiscard__]]//' -i lib/config.hin

    sed 's/test-stdalign\$(EXEEXT) //' -i tests/Makefile.in

}

build() {
    cd ${pkgname}-${pkgver}

    local configure_args=(
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
}

package() {
    cd ${pkgname}-${pkgver}

    make DESTDIR=${pkgdir} install
}

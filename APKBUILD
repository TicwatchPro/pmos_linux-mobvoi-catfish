# Reference: <https://postmarketos.org/vendorkernel>
# Kernel config based on: arch/arm/configs/catfish_defconfig
# Maintainer: Tipz Team <rcheung844@gmail.com>

pkgname=linux-mobvoi-catfish
pkgver=3.18.120
pkgrel=0
pkgdesc="Mobvoi Ticwatch Pro kernel fork"
arch="armv7"
_carch="arm"
_flavor="mobvoi-catfish"
url="https://kernel.org"
license="GPL-2.0-only"
options="!strip !check !tracedeps pmb:cross-native"
makedepends="bash bc bison devicepkg-dev flex openssl-dev perl"

# Source
_repository="android_kernel_mobvoi_catfish"
_commit="550d25dc2886a94e1ce08a7e0ac0db22d5609800"
_config="config-$_flavor.$arch"
source="
	$pkgname-$_commit.tar.gz::https://github.com/TipzTeam/$_repository/archive/$_commit.tar.gz
	$_config
"
builddir="$srcdir/$_repository-$_commit"
_outdir="out"

prepare() {
	default_prepare
	. downstreamkernel_prepare
}

build() {
	unset LDFLAGS
	make O="$_outdir" ARCH="$_carch" CC="${CC:-gcc}" \
		KBUILD_BUILD_VERSION="$((pkgrel + 1 ))-postmarketOS"
}

package() {
	downstreamkernel_package "$builddir" "$pkgdir" "$_carch" "$_flavor" "$_outdir"
}

sha512sums="45417f5dc6cd27ad48e3f83e1c4f30d6b05465564e7f6b81350fa385cb78cb1debeeafa85ba75b0b97b8f58ff6ca13dc884d48625708c367dde96bc086738194  linux-mobvoi-catfish-f7b56c62f51e6ef47aaa23235ad41ade38585ccd.tar.gz
6ee31a7f3fbaddcd3b188e0033f29b1c74fecccb475b4f020fb84f040f7b3bea6044eb50a7db5eab710a3905dfb522a70ab1cfeb0407255e2c22daa5d2b40858  config-mobvoi-catfish.armv7"

# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=php5-composer
_pkgrealname=composer
pkgver=1.1.3
pkgrel=0
pkgdesc="Dependency Manager for PHP"
url="https://getcomposer.org"
arch="noarch"
license="MIT"
depends="php5-cli php5-json php5-phar php5-zlib"
depends_dev="php5-dev"
makedepends="$depends_dev php5-dom php5-openssl"
install=""
source="$pkgname-$pkgver.tar.gz::https://github.com/$_pkgrealname/$_pkgrealname/archive/$pkgver.tar.gz
		$pkgname-$pkgver.phar::https://getcomposer.org/download/$pkgver/$_pkgrealname.phar
		change-php-executable-name.patch"

builddir="$srcdir/$_pkgrealname-$pkgver"

prepare() {
	cd "$builddir"
	for i in $source; do
		case $i in
		*.patch)
			msg "Applying ${i}"; patch -p1 -i "$srcdir/$i" || return 1;;
		esac
	done
}

build() {
	cd "$builddir"
	msg "Installing dependencies via $pkgname-$pkgver.phar"
	php5 "$srcdir"/$pkgname-$pkgver.phar install --ansi --prefer-dist --quiet
	msg "Compiling executable"
	php5 -d phar.readonly=0 bin/compile
}

package() {
	cd "$builddir"
	install -Dm755 "$builddir"/$_pkgrealname.phar "$pkgdir"/usr/bin/$_pkgrealname
}

sha512sums="d90ad3accecb372a77025e383ae4a0cdfcac222bed4f6cb955953d3e7aa2d8406fa4896fb26ca22f1acd79e372d80e0f1cd92417ad85df52ab5ba90f930abd94  php5-composer-1.1.3.tar.gz
baab18cb942a85f89cbd1cd6f89eecc1d549a017ac32c7e6eaad17cc60b14a3c571e62821b0379b6d3a18c17b1347b3bb451059e227f47b8b774053a8f0ba6af  php5-composer-1.1.3.phar
07488249a8979ab8c9e82b743e2e25777c8bc2dee3daf2dc2c6412d7685c15b75dbadb631ed2923bba01dbee3e3d62a99df6d06b05dddfd429649a11f0a70bf6  change-php-executable-name.patch"

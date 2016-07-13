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
depends_dev=""
makedepends="$depends_dev"
install=""
source="$pkgname-$pkgver.phar::https://getcomposer.org/download/$pkgver/$_pkgrealname.phar"

builddir="$srcdir"

build() {
	return 0
}

package() {
	cd "$builddir"
	install -Dm755 "$srcdir"/$pkgname-$pkgver.phar "$pkgdir"/usr/bin/$_pkgrealname
}

md5sums="ed44158d1dc5acc48e0475f33781442b  php5-composer-1.1.3.phar"
sha256sums="4349ef555c8478b8fe148b10957bc40d696ce7b8cdeb7d50d3d684a854dca5cc  php5-composer-1.1.3.phar"
sha512sums="baab18cb942a85f89cbd1cd6f89eecc1d549a017ac32c7e6eaad17cc60b14a3c571e62821b0379b6d3a18c17b1347b3bb451059e227f47b8b774053a8f0ba6af  php5-composer-1.1.3.phar"

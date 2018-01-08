# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=php5-composer
_pkgrealname=composer
pkgver=1.6.2
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
		01-change-php-executable-name.patch
		02-set-compile-timestamp.patch
		03-set-version-info.patch"

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

sha512sums="0569c6876bfb30bdec1731718fa5d21d34fa7ecd0d1fd99fe02caf73cb2631145ff7604a374c4b14dc91d5d8e8acf3ab0c52f0f7c6c11b63130a21db516c1391  php5-composer-1.6.2.tar.gz
6706b9ba03e5f1db57285f701e89fc54f2a1b3d6aa64a921699fcd0725a6e80bf659b7aaf7a49fd6a7b3f3521180ea2db2a59282b5b817812635f69d2969d73e  php5-composer-1.6.2.phar
bc4d8ac6f3b1b0fb39a65cfab3686414fbdc77ba2533b6ca2815f4e7c0076f871e9bda7cef130ededdef1fa48c003126241d3ee78fa58d993059e184bb589712  01-change-php-executable-name.patch
cc47f5a2f4538d9a4600118b18014d30a62086209cb524282c01d6756853817ca91ff1b1ca619871dc57a247b61e1a80bbcd3162cfaf69d1e4c4b3dd70d50c3c  02-set-compile-timestamp.patch
2748e495b39d18b352ce848af0c3905f815826b380bb380df98d47d2d712cf9b78d6419117183506c70f22f1cbf0b09563f5392b6dea6d6320fdf239389632e1  03-set-version-info.patch"

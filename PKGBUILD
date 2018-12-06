# Contributor: Matheus de Alcantara <matheus.de.alcantara@gmail.com>

pkgname=mandoc
pkgver=1.14.4
pkgrel=2
pkgdesc='A suite of tools compiling mdoc from the OpenBSD project'
arch=('i686' 'x86_64')
url='https://mdocml.bsd.lv/'
license=('custom: ISC')
depends=('zlib')
provides=('')
conflicts=('')
source=("https://mdocml.bsd.lv/snapshots/$pkgname-$pkgver.tar.gz"
        'configure.local'
        'mandoc.service'
        'mandoc.timer')
sha256sums=('24eb72103768987dcc63b53d27fdc085796330782f44b3b40c4660b1e1ee9b9c'
            'ea5d5bcf04e48e04693fd99b8009cda202932f2af2abe671e1cb8cb7282f21bc'
            '2091411d5f87a3c371a5ba74b4773d1e454046446fa2cb045485979e52419bb6'
            '74d6a02b97a17fffddcc0a3dc830e811348b1f6c6b84f867882c776d50f00ea4')

prepare() {
	cp "$srcdir"/configure.local $pkgname-$pkgver
}

build() {
	cd $pkgname-$pkgver
	./configure
	make
}

package() {
	cd $pkgname-$pkgver
	DESTDIR="$pkgdir" make install
	# install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	# install -Dm644 "$srcdir"/mandoc.timer "$pkgdir"/usr/lib/systemd/system/mandoc.timer
	# install -Dm644 "$srcdir"/mandoc.service "$pkgdir"/usr/lib/systemd/system/mandoc.service
	# install -dm755 "$pkgdir"/usr/lib/systemd/system/multi-user.target.wants
	# ln -s ../mandoc.timer "$pkgdir"/usr/lib/systemd/system/multi-user.target.wants/mandoc.timer
}

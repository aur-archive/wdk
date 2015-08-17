
# Maintainer: Henry J. Wylde <accounts+aur at hjwylde dot com>

pkgname=wdk
pkgver=0.3.31
pkgrel=1
pkgdesc='Whiley Development Kit'
arch=('any')
url='http://whiley.org/'
license=('BSD')
depends=('java-runtime>=6' 'bash')
provides=("whiley-environment=$pkgver")
conflicts=('whiley-environment')
source=("http://whiley.org/download/wdk/wdk-src-v$pkgver.tgz" "wdk-src-local.tgz")
md5sums=('e7deb719d99c4477dc80e2aad8c8187c'
         '63e2c63824e9f7bd1351718d44025ab3')

package() {
    # Install local files
    cd "$srcdir/$pkgname-src-local"

    mkdir -p "$pkgdir/etc/profile.d/"
    install -m755 etc/profile.d/* "$pkgdir/etc/profile.d/"

    mkdir -p "$pkgdir/usr/bin/"
    ln -s $(ls bin/ | sed 's/.*/\/usr\/lib\/wdk\/bin\/&/') "$pkgdir/usr/bin/"
    rm "$pkgdir/usr/bin/wy_common.bash"

    mkdir -p "$pkgdir/usr/lib/$pkgname/bin/"
    install -m755 bin/* "$pkgdir/usr/lib/$pkgname/bin/"

    install -Dm644 usr/share/vim/vimfiles/syntax/whiley.vim \
            "$pkgdir/usr/share/vim/vimfiles/syntax/whiley.vim"


    # Install package files
    cd "$srcdir/$pkgname-v$pkgver"

    mkdir -p "$pkgdir/usr/lib/$pkgname/lib/"
    install -m644 lib/* "$pkgdir/usr/lib/$pkgname/lib/"

    install -Dm644 CONTRIBUTORS "$pkgdir/usr/share/doc/$pkgname/CONTRIBUTORS"
    install -Dm644 README "$pkgdir/usr/share/doc/$pkgname/README"

    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}


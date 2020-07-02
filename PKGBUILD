# Maintainer: Helle Vaanzinn <glitsj16 at riseup dot net >

pkgname=firejail-handler-http
pkgver=0.1.0
pkgrel=1
pkgdesc="HTTP(S) URL handler for Firejail"
arch=(x86_64)
license=(GPL2)
url="https://github.com/glitsj16/firejail-handler-http"
depends=('firejail' 'inotify-tools' 'xdg-utils')
# package contains only text files
options=(libtool !purge staticlibs !strip !zipman)
install=firejail-handler-http.install
_commit=14f27ff50cf3e8a71ecd0f4ae0266eb8c1be8093  # initial release
source=("git+https://github.com/glitsj16/firejail-handler-http.git#commit=${_commit}")
sha256sums=('SKIP')

package() {
    cd "$pkgname"

    # main scripts
    for _script in "firejail-handler-http" "firejail-handler-http-ctl"; do
        install -Dm755 "$_script" "$pkgdir"/usr/bin/${_script}
    done
    # common script settings
    install -Dm644 firejail-handler-settings-http.inc "$pkgdir"/usr/bin/firejail-handler-settings-http.inc
    # xdg-open wrapper
    install -Dm755 firejail-xdg-open "$pkgdir"/usr/local/bin/xdg-open
    # XDG autostart file
    install -Dm644 firejail-handler-http-ctl.desktop "$pkgdir"/etc/xdg/autostart/firejail-handler-http-ctl.desktop
    # license
    install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/${pkgname}/LICENSE
}

pkgname=yubikey-challange-response-disk-encryption
pkgver=1
pkgrel=1
plgdesc='Package to enroll and unlock LUKS containers with yubikey challange-response system where challange compromises of user password and UUID of partition'
arch=('any')
license=('GPL')
depends=('bash' 'yubikey-personalization' 'yubikey-manager' 'util-linux' 'coreutils' 'expect' 'gawk')
url='https://github.com/peto59/yubikey-challange-response-disk-encryption'
backup=('/etc/yubikey-challange-response-disk-encryption/ykchrde.conf')
source=('git+https://github.com/peto59/yubikey-challange-response-disk-encryption.git')

pkgver() {
  cd "${pkgname}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}


package() {
    install -d "$pkgdir/etc/${pkgname}"
    install -Dm644 ykchrde.conf "$pkgdir/etc/${pkgname}/ykchrde.conf"

    install -d "$pkgdir/usr/bin/${pkgname}"
    install -Dm755 ykchrde.sh "$pkgdir/usr/bin/ykchrde.sh"

    install -Dm644 hooks/ykchrde "$pkgdir/usr/lib/initcpio/hooks/ykchrde"

    install -Dm644 install/ykchrde "$pkgdir/usr/lib/initcpio/install/ykchrde"
    install -Dm644 install/sd-ykchrde "$pkgdir/usr/lib/initcpio/install/sd-ykchrde"
}

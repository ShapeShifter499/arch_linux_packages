# Maintainer: Joey Dumont     <joey.dumont@gmail.com>
# Maintainer: Bjorn Neergaard <bjorn@neersighted.com>
# Contributor: Danny Su       <contact@dannysu.com>

pkgname=duplicati-latest
pkgver=2.0.1.65
pkgrel=1
_date=2017-06-09
kgdesc='A free backup client that securely stores encrypted, incremental, compressed backups on cloud storage services and remote file servers'
url='http://duplicati.com'
license=('LGPL')
install='duplicati.install'
source=(https://github.com/duplicati/duplicati/releases/download/v${pkgver}-${pkgver}_canary_${_date}/duplicati-${pkgver}_canary_${_date}.zip
        duplicati.service
	duplicati-user.service)
sha256sums=('d19f15810154aaaf008af147ce6ef005c31480148ac03dc086a5ba4b1db6bd98'
            '3237249cb9de137c3284a5cd92a451f3a49ec2183c6254be4b5ef7969e04e4a1'
            '1a29b9d83f70cb98927bdc0116d1d9f160d2d9ab1de63ce29bd99c3a3842a54b')
arch=('i686' 'x86_64')
depends=('gtk-sharp-2' 'mono')

package() {
  # Install the service.
  install -Dm644 duplicati.service  "${pkgdir}/usr/lib/systemd/system/duplicati.service"
  install -Dm644 duplicati-user.service  "${pkgdir}/usr/lib/systemd/user/duplicati.service"
  rm duplicati.service duplicati-user.service

  # Install the program.
  rm *.zip
  mkdir -p "${pkgdir}/opt/duplicati-latest"
  cp -r . "${pkgdir}/opt/duplicati-latest"
}

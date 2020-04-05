# Maintainer: Mijail Rondon Viloria (mijailr)
# Special thanks: Fademind, pedrogabriel

pkgname=wd719x-firmware
pkgver=1
pkgrel=6
pkgdesc="Driver for Western Digital WD7193, WD7197 and WD7296 SCSI cards"
url="https://github.com/mijailr/wd719x-firmware"
license=('unknown')
makedepends=('lha')
arch=('any')
conflicts=()
replaces=()
backup=()
source=('https://web.archive.org/web/20150802061047/http://support.wdc.com/download/archive/pciscsi.exe')
sha256sums=('d310338eaaeae6db3673021c0ec2ec23b9cfb9f9b9d1eb8854d2d60b3a6490f9')
noextract=('pciscsi.exe')

build() {
        lha xi pciscsi.exe pci-scsi.exe
        lha xi pci-scsi.exe nt/wd7296a.sys
        dd if=wd7296a.sys of=wd719x-risc.bin bs=1 skip=5760 count=14336
        dd if=wd7296a.sys of=wd719x-wcs.bin bs=1 skip=20096 count=514
}

package() {
        install -Dm644 $srcdir/wd719x-risc.bin $pkgdir/usr/lib/firmware/wd719x-risc.bin
        install -Dm644 $srcdir/wd719x-wcs.bin $pkgdir/usr/lib/firmware/wd719x-wcs.bin
}

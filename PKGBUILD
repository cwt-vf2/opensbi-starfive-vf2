# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>

pkgname=opensbi-6.6-starfive-vf2
pkgver=5.12.0
pkgrel=1
pkgdesc='OpenSBI for Linux 6.6.x (-cwt) for StarFive RISC-V VisionFive 2 Board'
_tag=JH7110_VF2_6.6_v${pkgver}
_srcname=opensbi-$_tag
url="https://github.com/starfive-tech/opensbi/"
arch=(riscv64)
license=('BSD-2-Clause')
provides=('opensbi')
conflicts=('opensbi')
makedepends=(gcc)
options=('!strip')
source=("${url}archive/refs/tags/${_tag}.tar.gz")

sha256sums=('b17d400f79784b92d54092a5a36f240e156709b6c9f5603bba661d590fbe109d')


prepare() {
  cd $_srcname
}

build() {
  cd $_srcname
  make -j $(nproc) \
    CC="gcc -mcpu=sifive-u74 -mtune=sifive-7-series" \
    PLATFORM=generic \
    FW_TEXT_START=0x40000000 \
    FW_OPTIONS=0
}

package() {
  cd $_srcname
  mkdir -p ${pkgdir}/usr
  make PLATFORM=generic I=${pkgdir}/usr install
  mv ${pkgdir}/usr/lib64 ${pkgdir}/usr/lib
}

# vim:set ts=8 sts=2 sw=2 et:

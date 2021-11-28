# Merged with official ABS kuserfeedback PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Martin Stolpe <martin dot stolpe at gmail dot com>
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=kuserfeedback-git
pkgver=1.0.0_r709.g3cf9f38
pkgrel=1
pkgdesc="Framework for collecting user feedback for applications via telemetry and surveys"
arch=($CARCH)
url="https://kde.org/products/frameworks/"
license=(GPL)
depends=(qt5-base)
makedepends=(git extra-cmake-modules-git qt5-tools clang qt5-charts qt5-svg qt5-declarative)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('qt5-declarative: QML bindings' 'qt5-charts: User Feedback console' 'qt5-svg: User Feedback console')
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'project(KUserFeedback' CMakeLists.txt | sed 's/.* //g' | tr - .)"
  echo "${_ver%)}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

#!/bin/bash

# Based on original PKGBUILD by Jacek Szafarkiewicz <szafar at linux dot pl>, Antonio Rojas <arojas@archlinux.org> and Andrea Scarpino <andrea@archlinux.org>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/orgs/Archiv8/kdevelop-python/discussions>
# Contributor: Ross Clark <https://github.com/orgs/Archiv8/kdevelop-python/discussions>

pkgname="kdevelop-python"
pkgver=22.08.1
pkgrel=3
pkgdesc="Python language and documentation plugin for KDevelop"
arch=(
  "x86_64"
)
url="http://www.kdevelop.org/"
license=(
  "GPL"
)
depends=(
  #Official Repositories
  "kdevelop"

  # Archiv8 / AUR Repositories
  # [Fixes]: Build error indicating missing node.h
  "python39"
)
makedepends=(
  #Official Repositories
  "extra-cmake-modules"
)
optdepends=(
  #Official Repositories
  "python-pycodestyle: for Python style checking"
)
groups=(
  "kde-applications"
  "kdevelop"
)
source=(
  "https://download.kde.org/stable/release-service/$pkgver/src/kdev-python-$pkgver.tar.xz"
)
sha512sums=(
  "a15946b2dfc0242ba4d4f2d22cd30631a17b060dec5ee13569529bb17fc892d25b048ab12899efd8e1db81f9399fd706fbe18f16d46d74e58b6eac43f559bd8c"
)
# validpgpkeys=(CA262C6C83DE4D2FB28A332A3A6A4DB839EAA6D7  # Albert Astals Cid <aacid@kde.org>
#               F23275E4BF10AFC1DF6914A6DBD2CE893E2D1C87  # Christoph Feck <cfeck@kde.org>
#               D81C0CB38EB725EF6691C385BB463350D6EF31EF) # Heiko Becker <heiko.becker@kde.org>

build() {
  cd kdev-python-$pkgver
  cmake -B build -S . \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  cd kdev-python-$pkgver
  DESTDIR="$pkgdir" cmake --install build
}

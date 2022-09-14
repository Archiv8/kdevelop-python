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

# Maintainer: Ross Clark <https://github.com/orgs/Archiv8/cinelerra-gg/discussions>
# Contributor: Ross Clark <https://github.com/orgs/Archiv8/cinelerra-gg/discussions>


pkgname=kdevelop-python
pkgver=21.12.0
pkgrel=2
pkgdesc="Python language and documentation plugin for KDevelop"
arch=(x86_64)
url="http://www.kdevelop.org/"
license=(GPL)
depends=(kdevelop 'python<3.10')
makedepends=(extra-cmake-modules)
optdepends=('python-pycodestyle: for Python style checking')
groups=(kde-applications kdevelop)
source=(https://download.kde.org/stable/release-service/$pkgver/src/kdev-python-$pkgver.tar.xz{,.sig})
sha256sums=('9dddb76e6d7bb61605839217609cc864b95e8f4524c4f2499f5911c9d76ece0a'
            'SKIP')
validpgpkeys=(CA262C6C83DE4D2FB28A332A3A6A4DB839EAA6D7  # Albert Astals Cid <aacid@kde.org>
              F23275E4BF10AFC1DF6914A6DBD2CE893E2D1C87  # Christoph Feck <cfeck@kde.org>
              D81C0CB38EB725EF6691C385BB463350D6EF31EF) # Heiko Becker <heiko.becker@kde.org>

build() {
  cmake -B build -S kdev-python-$pkgver \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
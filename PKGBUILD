# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Maintainer: Jan Alexander Steffens (heftig) <heftig@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_proj="mallard"
_pkg="ducktype"
pkgname="${_proj}-${_pkg}"
pkgver=1.0.2
pkgrel=12
_pkgdesc=(
  "Parser for the lightweight"
  "Ducktype syntax for Mallard."
)
url="http://project${_proj}.org"
arch=(
  'any'
)
license=(
  'MIT'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  "git"
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools"
  "${_py}-wheel"
)
_http="https://github.com"
_ns="project${_proj}"
_url="${_http}/${_ns}/${pkgname}"
source=(
  "git+${_url}?signed#tag=${pkgver}"
)
b2sums=(
  '52e3a2e45ac5eaff7e2aed73177088238b9bb9bb45025259fd9814aa676e5c9c1f2d726493d6a67b6d2cd334afb393a5f67d06fffab403a37eae243732d1be38'
)
validpgpkeys=(
  # Shaun McCance <shaunm@gnome.org>
  '4E03CB89E1C8ED8E049367ABE5D9AD24CC3ADF80'
)

build() {
  cd \
    "${pkgname}"
  "${_py}" \
    -m \
      build \
      --wheel \
      --no-isolation
}

package() {
  cd \
    "${pkgname}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    "dist/"*".whl"
  install \
    -Dt \
    "${pkgdir}/usr/share/licenses/${pkgname}" \
    -m644 \
    "COPYING"
}

# vim:set sw=2 sts=-1 et:

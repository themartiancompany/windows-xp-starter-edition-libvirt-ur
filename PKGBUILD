# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>

#    ----------------------------------------------------------------------
#    Copyright © 2022, 2023, 2024, 2025  Pellegrino Prevete
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


# shellcheck disable=SC2034
_py="python"
_pkg="windows-xp"
_variant="starter-editior"
_pkgbase="${_pkg}-${variant}"
_pkgname="${_pkgbase}"
pkgname=(
  "${_pkgname}-libvirt"
)
pkgver="1.0"
pkgrel=1
pkgdesc="Fifth version of Windows (libvirt VM)."
arch=(
  'any'
)
license=(
  'EULA'
)
url="https://web.archive.org/web/20030621141136/http://www.microsoft.com:80/italy/windowsxp/default.asp"
provides=(
  "${_pkgname}-libvirt"
)
depends=(
  "${_pkgname}"
  "libvirt"
)
makedepends=(
  "${_py}"
)
checkdepends=(
)
source=(
  "${_pkgname}-template.xml"
  "${_pkgname}-storage-template.xml"
  "uuidgen"
)
sha256sums=(
  'ce0d063cd127a6e8a89b525a2c2849c07e78ec5bfd85188ce66c8cb821e4d41e'
  '7ff294515b7c0f592ee108ffd61758a9234119ab9da3cea96e714911fea7ed5c'
  'a62d9a8c88926a4635268edcb428cf3616091f1ec453d6c449d05b651065776b'
)

prepare() {
  local \
    _uuidgen
  _uuidgen="${srcdir}/uuidgen"
  chmod \
    +x \
    "${_uuidgen}"
  sed \
    "s|%UUID%|$("${_uuidgen}")|g" \
    "${_pkgname}-template.xml" > \
    "${_pkgname}.xml"
  sed \
    "s|%UUID%|$("${_uuidgen}")|g" \
    "${_pkgname}-storage-template.xml" > \
    "${_pkgname}-storage.xml"
}



## shellcheck disable=SC2154
package() {
  local \
    _libvirt \
    _qemu \
    _storage
  _libvirt="${pkgdir}/etc/libvirt"
  _qemu="${_libvirt}/qemu"
  _storage="${_libvirt}/storage"
  install \
    -dm755 \
    "${_qemu}"
  install \
    -dm755 \
    "${_storage}"
  install \
    -Dm644 \
    "${_pkgname}.xml" \
    "${_qemu}/${_pkgname}.xml"
  install \
    -Dm644 \
    "${_pkgname}-storage.xml" \
    "${_storage}/${_pkgname}.xml"
}

# Maintainer: Cedric MATHIEU <me.xenom @ gmail.com>
# Contributor : Det <nimetonmaili @ gmail.com>
# Contributor: coderoar <coderoar @ gmail.com>
# Contributor: kang <kang @ mozilla.com>
# Contributor: chliny < chliny11 @ gmail.com>

_name=firefox
_channel=nightly
_area=zh-CN
pkgname="${_name}-${_channel}-zh"
pkgdesc='Standalone web browser from mozilla.org, nightly build'
url='http://www.mozilla.org/projects/firefox'
pkgver=30.0a1
_version=30.0a1
pkgrel=1
arch=('i686' 'x86_64')
license=('MPL' 'GPL' 'LGPL')
_file="${_name}-${_version}.${_area}.linux-${CARCH}"
_srcurl="https://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central-l10n/"
source=("${_srcurl}/${_file}.tar.bz2" 'firefox-nightly.desktop' 'firefox-nightly-safe.desktop')
_srcsum="$(curl -vs "${_srcurl}/${_file}.checksums" 2>&1 | grep bz | grep sha512 | cut -d " " -f1)"
sha512sums=(
"${_srcsum}" 
'08a9866d90339248f8c470078def84978ec9091e387674dc3b318758251ac2e603b2d16f798136665ef41eb046d6ca9dca7380ab076593a6b0781c044d043cf2'
'7f25f9c71a12327df61dced119530250c8b12781fddf683ee022e054398f0779645c8a416b56e6b580dc6cbcab7076439c6f78a297b9c7b4d5714209e4cb8824')
depends=('alsa-lib' 'libxt' 'libnotify' 'mime-types' 'nss' 'gtk2' 'sqlite' 'dbus-glib')

package() {
  
  # uncomment these lines to enable GnuPG signature verification. You'll need Firefox's GnuPG release key.
  # Their current fingerprint is 2B90 598A 745E 992F 315E  22C5 8AB1 3296 3A06 537A shortid 0x15A0A4BC
  #msg "Verifying GnuPG signature..."
  #FX_GPG="${_file}.checksums.asc"
  #FX_GPG_URI="${_srcurl}/${FX_GPG}"
  #FX_CHKSUM_URI="${_srcurl}/${_file}.checksums"
  #curl -OR ${FX_CHKSUM_URI}
  #curl -OR ${FX_GPG_URI} 
  #gpg --verify ${FX_GPG} 

  #  uncomment this line to remove these
  #  rm -rf firefox/{extensions,plugins,searchplugins}
  install -d "${pkgdir}"/{usr/{bin,share/{applications,pixmaps}},opt}
  cp -r firefox "${pkgdir}/opt/firefox-${pkgver}"

  ln -s /opt/firefox-${pkgver}/firefox "${pkgdir}/usr/bin/firefox-nightly"
  install -m644 "${srcdir}"/{firefox-nightly.desktop,firefox-nightly-safe.desktop} "${pkgdir}/usr/share/applications/"
  install -m644 "${srcdir}/firefox/browser/icons/mozicon128.png" "${pkgdir}/usr/share/pixmaps/${pkgname}-icon.png"
}

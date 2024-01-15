pkgname=vkv-git
pkgver=r16.10845c0
pkgrel=1
arch=(any)

pkgdesc='Minimalistic tool to get secrets from a HashiCorp Vault KV store'
url='https://github.com/martinwe-adfinis/vkv'
license=(GPL)

makedepends=(coreutils git gzip)

provides=(vkv)
conflicts=(vkv)

source=('git+https://github.com/martinwe-adfinis/vkv')
sha256sums=(SKIP)

pkgver() {
  cd vkv
  printf 'r%d.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  depends=(coreutils glibc jq sh vault)
  optdepends=(
    'dmenu: for vkvmenu'
    'libnotify: for vkv -c and vkvmenu'
    'xclip: for vkvmenu and/or clipboard support'
    'xdotool: for vkvmenu -t'
  )

  cd vkv
  install -Dm0755 vkv "$pkgdir"/usr/bin/vkv
  install -Dm0755 vkvmenu "$pkgdir"/usr/bin/vkvmenu
  install -Dm0644 vkv.1 "$pkgdir"/usr/share/man/man1/vkv.1
  install -Dm0644 vkvmenu.1 "$pkgdir"/usr/share/man/man1/vkvmenu.1
  install -Dm0644 README.md "$pkgdir"/usr/share/doc/vkv/README.md
}

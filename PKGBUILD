pkgname=lvm-autosnap
pkgver=0.0.1
pkgrel=1
pkgdesc=''
arch=('any')
license=('MIT')
depends=('lvm2')
source=(
  'cli.sh'
  'config.sh'
  'core.sh'
  'install-hook.sh'
  'lvm-autosnap'
  'lvm-autosnap.env'
  'lvm-autosnap.service'
  'lvm-autosnap.timer'
  'lvm-wrapper.sh'
  'lvol.sh'
  'runtime-hook.sh'
  'util.sh'
)
backup=(etc/lvm-autosnap.env)

package() {
  # Add core scripts
  bin_dir="${pkgdir}/usr/share/lvm-autosnap"
  install -D -m0755 "${srcdir}/cli.sh" "$bin_dir/cli.sh"
  install -D -m0755 "${srcdir}/config.sh" "$bin_dir/config.sh"
  install -D -m0755 "${srcdir}/core.sh" "$bin_dir/core.sh"
  install -D -m0755 "${srcdir}/lvm-wrapper.sh" "$bin_dir/lvm-wrapper.sh"
  install -D -m0755 "${srcdir}/lvol.sh" "$bin_dir/lvol.sh"
  install -D -m0755 "${srcdir}/util.sh" "$bin_dir/util.sh"

  # Add the CLI
  install -D -m0755 "${srcdir}/lvm-autosnap" "${pkgdir}/usr/bin/lvm-autosnap"

  # Add default config file
  install -D -m0644 "${srcdir}/lvm-autosnap.env" "${pkgdir}/etc/lvm-autosnap.env"

    # Add service to mark snapshots as not-pending once successfully booted
  install -D -m0644 "${srcdir}/lvm-autosnap.service" "${pkgdir}/usr/lib/systemd/system/lvm-autosnap.service"
  install -D -m0644 "${srcdir}/lvm-autosnap.timer" "${pkgdir}/usr/lib/systemd/system/lvm-autosnap.timer"

  # Add the initcpio hooks
  install -D -m0644 "${srcdir}/install-hook.sh" "${pkgdir}/usr/lib/initcpio/install/lvm-autosnap"
  install -D -m0644 "${srcdir}/runtime-hook.sh" "${pkgdir}/usr/lib/initcpio/hooks/lvm-autosnap"
}

sha256sums=('6d7cc55427b9c3103514e513bc0c692238d54b535ca08ec0b56ba8bc8edc05cd'
            'd3a720019dc1476e092c93658e785281ec9a2020506a6aa309aa397e51e0f2a6'
            '15314f01b5962981ff06c7d4c83cb6bd211ad0799388eb5b3d9fa9182882a87b'
            '3768f5fd32b7dd9dfdeec92a017be947e1c8634e7570fd78bec534ef3b13e8ec'
            'bad472cc3f9112460bb60519923e5dea6efcd4da20e292a47549e322ce6eb029'
            '2f4740be82fd099192d49239d21423b8bcbaf55831c31258f29a1b8516e34760'
            'b1a9666c71ab8bc008b321a2ff4cab0ad5ead45a54ecb8c932e0fbda5dd1643f'
            'e8da40587043edc18744bd23b844edfac95f6766cf6b397fce5ddbb3560401c2'
            'bda5351c3e38688c79db2b92381fb6786a11f9664e8366bd45d5da72a83c6d96'
            '4a4050657eff45156637eb694a4190a63f6cc478e4507fff75913668fa9b14ff'
            'e2f29d12ffe02adff1896ec88bf5dd8ee45ce103ff71fc6522791097af76c66b'
            '86b2f40e8e66c9d351a71406178ce58ec6d62d288d397de9049f1b03c1373e57')


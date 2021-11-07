roms = []
if unpack_edk2_blobs
  fds = [
    'edk2-aarch64-code.fd',
    'edk2-arm-code.fd',
    'edk2-arm-vars.fd',
    'edk2-i386-code.fd',
    'edk2-i386-secure-code.fd',
    'edk2-i386-vars.fd',
    'edk2-x86_64-code.fd',
    'edk2-x86_64-secure-code.fd',
  ]

  foreach f : fds
    roms += custom_target(f,
                  build_by_default: have_system,
                  output: f,
                  input: files('@0@.bz2'.format(f)),
                  capture: true,
                  install: get_option('install_blobs'),
                  install_dir: qemu_datadir,
                  command: [ bzip2, '-dc', '@INPUT0@' ])
  endforeach
endif

blobs = [
  'openbios-sparc32',
  'openbios-sparc64',
  'openbios-ppc',
  'qemu-nsis.bmp',
  's390-ccw.img',
  's390-netboot.img',
  'skiboot.lid',
  'palcode-clipper',
  'u-boot.e500',
  'qemu_vga.ndrv',
  'edk2-licenses.txt',
  'hppa-firmware.img',
]

if get_option('install_blobs')
  install_data(blobs, install_dir: qemu_datadir)
endif

subdir('descriptors')
subdir('keymaps')

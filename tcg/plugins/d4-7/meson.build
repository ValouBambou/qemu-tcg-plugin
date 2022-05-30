dinero_src = ss.source_set()
dinero_data = configuration_data()
dinero_src = files(
  'ref.c',
  'misc.c',
  'cmdmain.c',
  'cmdargs.c',
  'tracein.c',
  'xdinfmt.c',
  'dinfmt.c',
  'binaryfmt.c',
  'pixie32fmt.c',
  'pixie64fmt.c',
)
configure_file(
  output: 'config.h',
  configuration: dinero_data
)
dinero_carg = [
  '-O2',
  # From qemu's own `meson.build`
  # FIXME: There does not seem to be a way to completely replace the c_args
  # that come from add_project_arguments() -- we can only add to them.
  # So: disable all warnings with a big hammer.
  '-Wno-error', '-w',
  '-DD4ADDR=uint64_t',
  '-include', 'stdint.h'
]

libdinero = static_library(
  'dineroIV',
  build_by_default: true,
  sources: dinero_src,
  pic: true,
  c_args: dinero_carg
)

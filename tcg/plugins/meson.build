plugin_carg = [
  '-O2',
]

plugin_link_arg = [
  '-Wl,-z,undefs' # Override Meson's default behaviour that fornids undefined refs in shared
                  # libraries, which is needed for the plugin interface
]

plugin_install_dir = 'usr/lib'

plugin_list = [
  'ftrace',
  'icount',
  'icount-inlined',
  'iomem-example',
  'oprofile',
  'parameters',
  'profile',
  'trace'
]

subdir('d4-7')
dinero_plugin_src = files(
 'dineroIV.c'
)

libdinero_plugin = shared_library('tcg-plugin-dineroIV-' + target,
  build_by_default: true,
  sources: dinero_plugin_src,
  link_with: libdinero,
  c_args: plugin_carg + c_args,
  link_args : plugin_link_arg,
  include_directories: ['d4-7'] + target_inc,
  install: true,
  install_dir: plugin_install_dir
)


dyncount_plugin_src = files(
 'dyncount.c'
)

libdyncount_plugin = shared_library('tcg-plugin-dyncount-' + target,
  build_by_default: true,
  sources: dyncount_plugin_src,
  dependencies: capstone,
  c_args: plugin_carg + c_args,
  link_args : plugin_link_arg,
  include_directories: target_inc,
  install: true,
  install_dir: plugin_install_dir
)


dyntrace_plugin_src = files(
 'dyntrace.c'
)

libdyntrace_plugin = shared_library('tcg-plugin-dyntrace-' + target,
  build_by_default: true,
  sources: dyntrace_plugin_src,
  dependencies: capstone,
  c_args: plugin_carg + c_args,
  link_args : plugin_link_arg,
  include_directories: target_inc,
  install: true,
  install_dir: plugin_install_dir
)

coverage_plugin_src = files(
 'coverage.c'
)

libcoverage_plugin = shared_library('tcg-plugin-coverage-' + target,
  build_by_default: true,
  sources: coverage_plugin_src,
  dependencies: capstone,
  c_args: plugin_carg + c_args,
  link_args : plugin_link_arg,
  include_directories: target_inc,
  install: true,
  install_dir: plugin_install_dir
)

foreach pl: plugin_list
  plugin_src = files(
    pl + '.c'
  )

  lib_plugin = shared_library('tcg-plugin-' + pl + '-' + target,
    build_by_default: true,
    sources: plugin_src,
    c_args: plugin_carg + c_args,
    link_args : plugin_link_arg,
    include_directories: target_inc,
    install: true,
    install_dir: plugin_install_dir
  )
endforeach

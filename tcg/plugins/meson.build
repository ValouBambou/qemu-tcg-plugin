tcg_plugin_carg = [
  '-O2',
]

tcg_plugin_link_arg = [
  '-Wl,-z,undefs' # Override Meson's default behaviour that fornids undefined refs in shared
                  # libraries, which is needed for the plugin interface
]

tcg_plugin_install_dir = 'usr/lib'

tcg_plugin_list = [
  'ftrace',
  'icount',
  'icount-inlined',
  'iomem-example',
  'oprofile',
  'parameters',
  'profile',
  'trace'
]

if 'CONFIG_TCG_PLUGIN_CPP' in config_host
  tcg_cpp_plugin_carg = [
    '-Wall',
    '-std=c++14'
  ]
  tcg_cpp_plugin_link_arg = []
  tcg_cpp_plugin_src = files(
    'cpp.c',
    'cpp/plugin_api.cpp',
    'cpp/count_instructions.cpp',
    'cpp/coverage.cpp',
    'cpp/print_dependences.cpp',
    'cpp/print_instructions.cpp',
    'cpp/program_profiler.cpp'
  )
endif

subdir('d4-7')

dinero_plugin_src = files(
 'dineroIV.c'
)

dyncount_plugin_src = files(
 'dyncount.c'
)

dyntrace_plugin_src = files(
 'dyntrace.c'
)

coverage_plugin_src = files(
 'coverage.c'
)

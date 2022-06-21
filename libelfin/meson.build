libelif_cxxargs = [
  '-O2',
  '-std=c++11',
  '-Wno-error' # Mandatory as removal of -Werror in CARGS is not possible is meson
]

libelf_files = files(
  'libelfin/elf/elf.cc',
  'libelfin/elf/mmap_loader.cc'
)
libelf_bin = static_library('elf',
                             build_by_default: false,
                             sources: libelf_files,
                             pic: true,
                             cpp_args: libelif_cxxargs,
                             include_directories: 'libelfin/elf/')
libelf = declare_dependency(link_with: libelf_bin,
                            include_directories: '.')

# Generate `libelfin/dwarf/to_string.cc`
run_command('gen_to_string.sh',
  'libelfin/dwarf/',
  check: true
)

libdwarf_files = files(
  'libelfin/dwarf/abbrev.cc',
  'libelfin/dwarf/attrs.cc',
  'libelfin/dwarf/cursor.cc',
  'libelfin/dwarf/die.cc',
  'libelfin/dwarf/die_str_map.cc',
  'libelfin/dwarf/dwarf.cc',
  'libelfin/dwarf/elf.cc',
  'libelfin/dwarf/expr.cc',
  'libelfin/dwarf/line.cc',
  'libelfin/dwarf/rangelist.cc',
  'libelfin/dwarf/to_string.cc',
  'libelfin/dwarf/value.cc'
)
libdwarf_bin = static_library('dwarf',
                             build_by_default: false,
                             sources: libdwarf_files,
                             pic: true,
                             cpp_args: libelif_cxxargs,
                             include_directories: 'libelfin/dwarf/')
libdwarf = declare_dependency(link_with: libdwarf_bin,
                              include_directories: '.')

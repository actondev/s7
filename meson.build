project('s7', 'c')

includes = include_directories('.')

# essentially i'm just copying the file
# default settings
configure_file(input : 'mus-config.h.in',
               output : 'mus-config.h',
	       copy: true,
	      )

# or.. no settings at all..?
# configure_file(configuration: configuration_data(),
#                output : 'mus-config.h')

system = host_machine.system()
compiler_id = meson.get_compiler('c').get_id()
# link_args = []
# if system == 'linux'
#   link_args = [
#   '-lm', # log, ceil etc
#   # '-ldl', # dlopen etc
#   ]
# elif system == 'windows'
#   # msvc vs gcc ??
#   if compiler_id == 'gcc'
#     link_args = [
#       '-lm', # log, ceil etc
#     ]
#   endif
# endif
# linux mingw?

link_args = [
  '-lm', # math
  ]

s7 = library('s7',
	     's7.c',
	     include_directories : includes,
	     c_args : [],
	     link_args : link_args,
	    )
s7_dep = declare_dependency(
  link_with : s7,
  include_directories : includes,
  link_args: link_args,
)

if not meson.is_subproject()
  repl = executable(
    'repl',
    sources: ['repl.c'],
    include_directories : includes,
    dependencies: [s7_dep,
		  ],
  )
  
endif

# building nrepl fails without the following mod:
# - adding #define __USE_MISC in nrepl.c before the line #include <glob.h>
# if not, there's an error GLOB_TILDE not defined
if get_option('nrepl')
  compiler = meson.get_compiler('c')
  cmake = import('cmake')
  notcurses_opt = cmake.subproject_options()
  notcurses_opt.add_cmake_defines({'USE_QRCODEGEN': false,
  				   'USE_MULTIMEDIA': 'none',
  				   'USE_DOCTEST': false,
  				   'USE_PANDOC': false})
  # set(CMAKE_CXX_STANDARD 17) ignored??
  notcurses_opt.set_override_option('cpp_std', 'c++17')
  notcurses_proj = cmake.subproject('notcurses', options: notcurses_opt)
  notcurses_dep = notcurses_proj.dependency('notcurses')

  nrepl = executable(
    'nrepl',
    sources: ['nrepl.c'],
    include_directories : includes,
    c_args: [
      # '-D__USE_MISC', # for glob.h GLOB_TILDE
  		  ],
    dependencies: [s7_dep,
  		   notcurses_dep,
  		  ],
  )
endif

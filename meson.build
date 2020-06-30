project('s7', 'c')

includes = include_directories('.')

sources = files(
 's7.c',
  )

# essentially i'm just copying the file
# conf_data = configuration_data()
# configure_file(input : 'mus-config.h.in',
#                output : 'mus-config.h',
#                configuration : conf_data)

configure_file(input : 'mus-config.h.in',
               output : 'mus-config.h',
               copy: true)

link_args = []

# todo windows
link_args += [
  '-lm', # log, ceil etc
  '-ldl', # dlopen etc
]

s7 = library('s7',
  sources,
  include_directories : includes,
  c_args : [],
  # link_args : link_args,
	    )
s7_dep = declare_dependency(
  link_with : s7,
  include_directories : includes,
  link_args: link_args,
)

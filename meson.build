project('s7', 'c')

includes = include_directories('.')

sources = files(
 #  'audio.c',
 # 'clm.c',
 # 'clm2xen.c',
 # 'configure.ac',
 # 'gl.c',
 # 'gl2ps.c',
 # 'glistener.c',
 # 'gtk-script.c',
 # 'headers.c',
 # 'io.c',
 # 'libarb_s7.c',
 # 'libgtk_s7.c',
 # 'repl.c',
 's7.c',
 # 'snd-axis.c',
 # 'snd-chn.c',
 # 'snd-completion.c',
 # 'snd-dac.c',
 # 'snd-data.c',
 # 'snd-draw.c',
 # 'snd-edits.c',
 # 'snd-env.c',
 # 'snd-fft.c',
 # 'snd-file.c',
 # 'snd-find.c',
 # 'snd-gchn.c',
 # 'snd-gdraw.c',
 # 'snd-genv.c',
 # 'snd-gfft.c',
 # 'snd-gfile.c',
 # 'snd-gfind.c',
 # 'snd-ghelp.c',
 # 'snd-glistener.c',
 # 'snd-gmain.c',
 # 'snd-gmenu.c',
 # 'snd-gmix.c',
 # 'snd-gprefs.c',
 # 'snd-gregion.c',
 # 'snd-gsnd.c',
 # 'snd-gutils.c',
 # 'snd-gxbitmaps.c',
 # 'snd-gxcolormaps.c',
 # 'snd-help.c',
 # 'snd-io.c',
 # 'snd-kbd.c',
 # 'snd-ladspa.c',
 # 'snd-listener.c',
 # 'snd-main.c',
 # 'snd-marks.c',
 # 'snd-menu.c',
 # 'snd-mix.c',
 # 'snd-motif.c',
 # 'snd-nogui.c',
 # 'snd-prefs.c',
 # 'snd-print.c',
 # 'snd-region.c',
 # 'snd-select.c',
 # 'snd-sig.c',
 # 'snd-snd.c',
 # 'snd-trans.c',
 # 'snd-utils.c',
 # 'snd-xen.c',
 # 'snd-xref.c',
 # 'snd.c',
 # 'sndinfo.c',
 # 'sndlib2xen.c',
 # 'sndplay.c',
 # 'sound.c',
 # 'vct.c',
 # 'xen.c',
 # 'xg.c',
 # 'xm.c',

  )

# essentially i'm just copying the file
conf_data = configuration_data()
configure_file(input : 'mus-config.h.in',
               output : 'mus-config.h',
               configuration : conf_data)


link_args = []

# todo windows
link_args += [
  '-lm', # log, ceil etc
  '-ldl', # dlopen etc
]

s7 = library('s7',
  sources,
  include_directories : includes,
  # c_args : core_args,
  link_args : link_args,
  # dependencies : core_deps,
	    )
s7_dep = declare_dependency(
  link_with : s7,
  include_directories : includes,
)

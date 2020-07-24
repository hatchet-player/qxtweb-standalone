# libqxt.core build file
#============================================================================

libqxt_core_dir = meson.current_source_dir()

# src
#============================================================================

# Ripped bits of QxtCore:
libqxt_src += files(
    join_paths(libqxt_core_dir, 'qxtmetaobject.cpp'),
    join_paths(libqxt_core_dir, 'qxtnull.cpp'),
    join_paths(libqxt_core_dir, 'qxtfifo.cpp'))


libqxt_h += files(
    join_paths(libqxt_core_dir, 'qxtboundcfunction.h'),
    join_paths(libqxt_core_dir, 'qxtmetaobject.h'),
    join_paths(libqxt_core_dir, 'qxtnull.h'))


libqxt_core_moc_h = files(
    join_paths(libqxt_core_dir, 'qxtboundfunction.h'),
    join_paths(libqxt_core_dir, 'qxtfifo.h'))


libqxt_moc += qt5.preprocess(
    moc_headers : libqxt_core_moc_h,
    include_directories : libqxt_inc)


# include directories
#============================================================================

libqxt_inc += include_directories('.')

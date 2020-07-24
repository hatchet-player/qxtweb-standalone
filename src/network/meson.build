# libqxt.network build file
#============================================================================

libqxt_network_dir = meson.current_source_dir()

# src
#============================================================================

# Ripped bits of QxtCore:
libqxt_src += files(
    join_paths(libqxt_network_dir, 'qxtsslserver.cpp'))


libqxt_network_moc_h = files(
    join_paths(libqxt_network_dir, 'qxtsslserver.h'))


libqxt_moc += qt5.preprocess(
    moc_headers : libqxt_network_moc_h,
    include_directories : libqxt_inc)


# include directories
#============================================================================

libqxt_inc += include_directories('.')

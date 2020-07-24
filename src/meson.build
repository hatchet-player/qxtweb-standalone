# thirdparty.qxt build file
#============================================================================

libqxt_dir = meson.current_source_dir()

# dependancies
#============================================================================

libqxt_dep_list = [
    qt5_dep,
    gnutls_dep]


# include directories
#============================================================================


# cpp source
#---------------------------------------------------
libqxt_src = files()
libqxt_h = files()


# src for qxt preprocessor
#---------------------------------------------------
libqxt_moc_src = files()
libqxt_moc_h = files()
libqxt_moc = [] 


# include directories
#============================================================================

libqxt_inc += include_directories('.', 'QxtWeb','QxtNetwork')

libqxt_dirs = [
    'core',
    'network',
    'web']


foreach dir : libqxt_dirs
    subdir(dir)
endforeach


# Link args
#============================================================================


libqxt_link_list = []


libqxt_link_args = []


# build
#============================================================================


libqxt_lib = library(
    'qxtweb-standalone',
    install : true,
    install_mode : 'rwxr-xr-x',
    install_dir : libdir,
    include_directories : libqxt_inc,
    sources : [
        libqxt_src,
        libqxt_moc],
    link_with : libqxt_link_list,
    link_args : libqxt_link_args,
    dependencies : libqxt_dep_list)

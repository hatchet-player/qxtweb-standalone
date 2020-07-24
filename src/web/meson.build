# libqxt.core build file
#============================================================================

libqxt_web_dir = meson.current_source_dir()

# src
#============================================================================


libqxt_src += files(
    join_paths(libqxt_web_dir, 'qhttpheader.cpp'),
    join_paths(libqxt_web_dir, 'qxtabstracthttpconnector.cpp'),
    join_paths(libqxt_web_dir, 'qxtabstractwebservice.cpp'),
    join_paths(libqxt_web_dir, 'qxtabstractwebsessionmanager.cpp'),
    join_paths(libqxt_web_dir, 'qxthtmltemplate.cpp'),
    join_paths(libqxt_web_dir, 'qxthttpserverconnector.cpp'),
    join_paths(libqxt_web_dir, 'qxthttpsessionmanager.cpp'),
    join_paths(libqxt_web_dir, 'qxtscgiserverconnector.cpp'),
    join_paths(libqxt_web_dir, 'qxtwebcontent.cpp'),
    join_paths(libqxt_web_dir, 'qxtwebevent.cpp'),
    join_paths(libqxt_web_dir, 'qxtwebservicedirectory.cpp'),
    join_paths(libqxt_web_dir, 'qxtwebslotservice.cpp'))


libqxt_h += files(
    join_paths(libqxt_web_dir, 'qhttpheader.h'),
    join_paths(libqxt_web_dir, 'qxthtmltemplate.h'),
    join_paths(libqxt_web_dir, 'qxtwebevent.h'))


libqxt_web_moc_h = files(
    join_paths(libqxt_web_dir, 'qxtabstracthttpconnector.h'),
    join_paths(libqxt_web_dir, 'qxtabstractwebservice.h'),
    join_paths(libqxt_web_dir, 'qxtabstractwebsessionmanager.h'),
    join_paths(libqxt_web_dir, 'qxtabstractwebsessionmanager_p.h'),
    join_paths(libqxt_web_dir, 'qxthttpsessionmanager.h'),
    join_paths(libqxt_web_dir, 'qxtwebcontent.h'),
    join_paths(libqxt_web_dir, 'qxtwebservicedirectory.h'),
    join_paths(libqxt_web_dir, 'qxtwebservicedirectory_p.h'),
    join_paths(libqxt_web_dir, 'qxtwebslotservice.h'))


libqxt_moc += qt5.preprocess(
    moc_headers : libqxt_web_moc_h,
    include_directories : libqxt_inc)


# include directories
#============================================================================

libqxt_inc += include_directories('.')

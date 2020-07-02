# thirdparty.qxt build file
#============================================================================


libqxt_dir = meson.current_source_dir()
libqxt_inc += include_directories('.', 'core','web', 'network')


libqxt_src = files(
    join_paths(libqxt_dir, 'web/qxtabstracthttpconnector.cpp'),
    join_paths(libqxt_dir, 'web/qxtabstractwebservice.cpp'),
    join_paths(libqxt_dir, 'web/qxtabstractwebsessionmanager.cpp'),
    join_paths(libqxt_dir, 'web/qxthtmltemplate.cpp'),
    join_paths(libqxt_dir, 'web/qxthttpserverconnector.cpp'),
    join_paths(libqxt_dir, 'web/qxthttpsessionmanager.cpp'),
    join_paths(libqxt_dir, 'web/qxtscgiserverconnector.cpp'),
    join_paths(libqxt_dir, 'web/qxtwebcontent.cpp'),
    join_paths(libqxt_dir, 'web/qxtwebevent.cpp'),
    join_paths(libqxt_dir, 'web/qxtwebservicedirectory.cpp'),
    join_paths(libqxt_dir, 'web/qhttpheader.cpp'),
    join_paths(libqxt_dir, 'web/qxtwebslotservice.cpp'),

    # Ripped bits of QxtCore:
    join_paths(libqxt_dir, 'core/qxtmetaobject.cpp'),
    join_paths(libqxt_dir, 'core/qxtnull.cpp'),
    join_paths(libqxt_dir, 'core/qxtfifo.cpp'),

    # QxtNetwork
    join_paths(libqxt_dir, 'network/qxtsslserver.cpp'),

    # automoc hack
    join_paths(libqxt_dir, 'core/qxtboundfunction.h'))

libqxt_moc_src = files()

libqxt_moc_h = files(
    join_paths(libqxt_dir, 'web/qxtabstracthttpconnector.h'),
    join_paths(libqxt_dir, 'web/qxtabstractwebservice.h'),
    join_paths(libqxt_dir, 'web/qxtabstractwebsessionmanager.h'),
    join_paths(libqxt_dir, 'web/qxtabstractwebsessionmanager_p.h'),
    join_paths(libqxt_dir, 'web/qxthtmltemplate.h'),
    join_paths(libqxt_dir, 'web/qxthttpsessionmanager.h'),
    join_paths(libqxt_dir, 'web/qxtwebcontent.h'),
    join_paths(libqxt_dir, 'web/qxtwebevent.h'),
    join_paths(libqxt_dir, 'web/qxtwebservicedirectory.h'),
    join_paths(libqxt_dir, 'web/qxtwebservicedirectory_p.h'),
    join_paths(libqxt_dir, 'web/qhttpheader.h'),
    join_paths(libqxt_dir, 'web/qxtwebslotservice.h'),

    # Ripped bits of QxtCore:
    join_paths(libqxt_dir, 'core/qxtmetaobject.h'),
    join_paths(libqxt_dir, 'core/qxtnull.h'),
    join_paths(libqxt_dir, 'core/qxtfifo.h'),

    # QxtNetwork
    join_paths(libqxt_dir, 'network/qxtsslserver.h'),

    # automoc hack
    join_paths(libqxt_dir, 'core/qxtboundfunction.h'))



# dependancies
#============================================================================

libqxt_dep_list = [
    qt5_dep,
    gnutls_dep]


# Link args
#============================================================================


libqxt_link_list = []


libqxt_link_args = []


# targets
#============================================================================


# don't ask me what happened here, i don't want to know
gen_header = '''
import sys, os, errno

out = os.path.dirname(sys.argv[2])
if not os.path.exists(out) and (out != '') :
    try:
        os.makedirs(os.path.dirname(sys.argv[2]))
    except OSError as exc: # Guard against race condition
        if exc.errno != errno.EEXIST:
            raise
with open(sys.argv[2],'w+') as w:
    data = '#include "{}"'.format(sys.argv[1])
    w.write(data)
'''

fancy_h = [
    [
        join_paths(libqxt_dir, 'network/qxtsslserver.h'),
        join_paths(libqxt_dir, 'QxtNetwork/QxtSslServer')],
    [
        join_paths(libqxt_dir, 'web/qxtabstracthttpconnector.h'),
        join_paths(libqxt_dir, 'QxtWeb/QxtHttpServerConnector')],
    [
        join_paths(libqxt_dir, 'web/qxthttpsessionmanager.h'), 
        join_paths(libqxt_dir, 'QxtWeb/HttpSessionManager')],
    [
        join_paths(libqxt_dir, 'web/qxthttpsessionmanager.h'),
        join_paths(libqxt_dir, 'QxtWeb/QxtHttpSessionManager')],
    [
        join_paths(libqxt_dir, 'web/qxtwebcontent.h'),
        join_paths(libqxt_dir, 'QxtWeb/QxtWebContent')],
    [
        join_paths(libqxt_dir, 'web/qxtwebslotservice.h'),
        join_paths(libqxt_dir, 'QxtWeb/QxtWebSlotService')],
    [
        join_paths(libqxt_dir, 'web/qxtwebevent.h'),
        join_paths(libqxt_dir, 'QxtWeb/QxtWebPageEvent')],
]


foreach x : fancy_h
    message(x[0], x[1])
    result = run_command([
        'python', '-c', gen_header, x[0], x[1]]).stdout().strip()
    #libqxt_src += files(x[1])
endforeach


libqxt_inc += include_directories('QxtWeb','QxtNetwork')


# build
#============================================================================


libqxt_moc = [] 
libqxt_moc += qt5.preprocess(
    moc_sources : libqxt_moc_src,
    moc_headers : libqxt_moc_h,
    include_directories : libqxt_inc)


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

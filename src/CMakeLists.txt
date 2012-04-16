add_definitions( "-DSMPLAYER2_VERSION=\"${SMPLAYER2_VERSION}\"" )
if( NOT WIN32 )
	add_definitions( "-DDATA_PATH=\"${CMAKE_INSTALL_PREFIX}/share/smplayer2\"" )
endif()

find_package( Qt4 REQUIRED QtCore QtGui QtNetwork QtXml )
find_package( ZLIB REQUIRED )
set( QT_USE_QTNETWORK TRUE )
set( QT_USE_QTXML TRUE )

include( ${QT_USE_FILE} )
add_definitions( ${QT_DEFINITIONS} )

# gui ---------------------------------------------------------------------->>>1
set( smplayer2_gui_SOURCES
	gui/basegui.cpp
	gui/baseguiplus.cpp
	gui/defaultgui.cpp
	gui/minigui.cpp
	gui/mpcgui/mpcgui.cpp
	gui/mpcgui/mpcstyles.cpp
)

set( smplayer2_gui_HEADERS
	gui/basegui.h
	gui/baseguiplus.h
	gui/defaultgui.h
	gui/minigui.h
	gui/mpcgui/mpcgui.h
	gui/mpcgui/mpcstyles.h
)

set( smplayer2_gui_NOMOC_HEADERS
	gui/guiconfig.h
)
#---------------------------------------------------------------------------<<<1
# prefui ------------------------------------------------------------------->>>1
set( smplayer2_prefui_SOURCES
	prefui/prefadvanced.cpp
	prefui/prefdrives.cpp
	prefui/preferencesdialog.cpp
	prefui/prefgeneral.cpp
	prefui/prefinput.cpp
	prefui/prefinterface.cpp
	prefui/prefperformance.cpp
	prefui/prefplaylist.cpp
	prefui/prefsubtitles.cpp
	prefui/preftv.cpp
)

set( smplayer2_prefui_HEADERS
	prefui/prefadvanced.h
	prefui/prefdrives.h
	prefui/preferencesdialog.h
	prefui/prefgeneral.h
	prefui/prefinput.h
	prefui/prefinterface.h
	prefui/prefperformance.h
	prefui/prefplaylist.h
	prefui/prefsubtitles.h
	prefui/preftv.h
)

set( smplayer2_prefui_FORMS
	prefui/prefadvanced.ui
	prefui/prefdrives.ui
	prefui/preferencesdialog.ui
	prefui/prefgeneral.ui
	prefui/prefinput.ui
	prefui/prefinterface.ui
	prefui/prefperformance.ui
	prefui/prefplaylist.ui
	prefui/prefsubtitles.ui
	prefui/preftv.ui
)
#---------------------------------------------------------------------------<<<1
# widgets ------------------------------------------------------------------>>>1
set( smplayer2_widgets_SOURCES
	widgets/actionseditor.cpp
	widgets/audioequalizer.cpp
	widgets/eqslider.cpp
	widgets/filechooser.cpp
	widgets/floatingwidget.cpp
	widgets/lineedit_with_icon.cpp
	widgets/logwindow.cpp
	widgets/mplayerwindow.cpp
	widgets/mycombobox.cpp
	widgets/mylineedit.cpp
	widgets/myslider.cpp
	widgets/mytablewidget.cpp
	widgets/playlist.cpp
	widgets/playlistdock.cpp
	widgets/prefwidget.cpp
	widgets/seekwidget.cpp
	widgets/selectcolorbutton.cpp
	widgets/timeslider.cpp
	widgets/tristatecombo.cpp
	widgets/verticaltext.cpp
	widgets/videoequalizer.cpp
)

set( smplayer2_widgets_HEADERS
	widgets/actionseditor.h
	widgets/audioequalizer.h
	widgets/eqslider.h
	widgets/filechooser.h
	widgets/floatingwidget.h
	widgets/lineedit_with_icon.h
	widgets/logwindow.h
	widgets/mplayerwindow.h
	widgets/mylineedit.h
	widgets/myslider.h
	widgets/playlist.h
	widgets/playlistdock.h
	widgets/seekwidget.h
	widgets/selectcolorbutton.h
	widgets/timeslider.h
	widgets/tristatecombo.h
	widgets/videoequalizer.h
)
set( smplayer2_widgets_FORMS
	widgets/eqslider.ui
	widgets/logwindowbase.ui
	widgets/seekwidget.ui
)

set( smplayer2_widgets_NOMOC_HEADERS
	widgets/mycombobox.h
	widgets/mytablewidget.h
	widgets/prefwidget.h
	widgets/verticaltext.h
)
#---------------------------------------------------------------------------<<<1
# dialogs ------------------------------------------------------------------>>>1
set( smplayer2_dialogs_SOURCES
	dialogs/about.cpp
	dialogs/errordialog.cpp
	dialogs/favoriteeditor.cpp
	dialogs/filedialog.cpp
	dialogs/filepropertiesdialog.cpp
	dialogs/inputdvddirectory.cpp
	dialogs/inputurl.cpp
	dialogs/shortcutgetter.cpp
	dialogs/timedialog.cpp
	dialogs/vdpauproperties.cpp
)

set( smplayer2_dialogs_HEADERS
	dialogs/about.h
	dialogs/errordialog.h
	dialogs/favoriteeditor.h
	dialogs/filepropertiesdialog.h
	dialogs/inputdvddirectory.h
	dialogs/inputurl.h
	dialogs/shortcutgetter.h
	dialogs/timedialog.h
	dialogs/vdpauproperties.h
)

set( smplayer2_dialogs_FORMS
	dialogs/about.ui
	dialogs/errordialog.ui
	dialogs/favoriteeditor.ui
	dialogs/filepropertiesdialog.ui
	dialogs/inputdvddirectory.ui
	dialogs/inputurl.ui
	dialogs/timedialog.ui
	dialogs/vdpauproperties.ui
)

set( smplayer2_dialogs_NOMOC_HEADERS
	dialogs/filedialog.h
)
#---------------------------------------------------------------------------<<<1
# main --------------------------------------------------------------------->>>1
set( smplayer2_SOURCES
	assstyles.cpp
	clhelp.cpp
	colorutils.cpp
	core.cpp
	desktopinfo.cpp
	deviceinfo.cpp
	discname.cpp
	extensions.cpp
	favorites.cpp
	filesettings.cpp
	filesettingsbase.cpp
	filesettingshash.cpp
	filters.cpp
	findsubtitles/findsubtitlesconfigdialog.cpp
	findsubtitles/findsubtitleswindow.cpp
	findsubtitles/osparser.cpp
	findsubtitles/simplehttp.cpp
	global.cpp
	helper.cpp
	images.cpp
	infofile.cpp
	infoprovider.cpp
	inforeader.cpp
	languages.cpp
	main.cpp
	mediadata.cpp
	mediasettings.cpp
	mplayerprocess.cpp
	myaction.cpp
	myactiongroup.cpp
	myclient.cpp
	myprocess.cpp
	myserver.cpp
	paths.cpp
	preferences.cpp
	recents.cpp
	smplayer2.cpp
	subtracks.cpp
	titletracks.cpp
	toolbareditor.cpp
	tracks.cpp
	translator.cpp
	tvlist.cpp
	tvsettings.cpp
	urlhistory.cpp
	videopreview/videopreview.cpp
	videopreview/videopreviewconfigdialog.cpp
	widgetactions.cpp
	${smplayer2_gui_SOURCES}
	${smplayer2_prefui_SOURCES}
	${smplayer2_widgets_SOURCES}
	${smplayer2_dialogs_SOURCES}
)

set( smplayer2_HEADERS
	core.h
	favorites.h
	filters.h
	findsubtitles/findsubtitlesconfigdialog.h
	findsubtitles/findsubtitleswindow.h
	findsubtitles/simplehttp.h
	inforeader.h
	languages.h
	mplayerprocess.h
	myactiongroup.h
	myprocess.h
	myserver.h
	tvlist.h
	videopreview/videopreview.h
	videopreview/videopreviewconfigdialog.h
	widgetactions.h
	${smplayer2_gui_HEADERS}
	${smplayer2_prefui_HEADERS}
	${smplayer2_widgets_HEADERS}
	${smplayer2_dialogs_HEADERS}
)

set( smplayer2_FORMS
	findsubtitles/findsubtitlesconfigdialog.ui
	findsubtitles/findsubtitleswindow.ui
	videopreview/videopreviewconfigdialog.ui
	${smplayer2_prefui_FORMS}
	${smplayer2_widgets_FORMS}
	${smplayer2_dialogs_FORMS}
)
#---------------------------------------------------------------------------<<<1
# no moc headers ----------------------------------------------------------->>>1
set( smplayer2_NOMOC_HEADERS
	audioequalizerlist.h
	config.h
	constants.h
	preferences.h
	${smplayer2_gui_NOMOC_HEADERS}
	${smplayer2_widgets_NOMOC_HEADERS}
	${smplayer2_dialogs_NOMOC_HEADERS}
)
#---------------------------------------------------------------------------<<<1

set( smplayer2_RESOURCES icons.qrc )
set( smplayer2_LIBS ${QT_LIBRARIES} ${ZLIB_LIBRARY} )

if( HAVE_DOWNLOAD_SUBS )
	add_definitions( -DDOWNLOAD_SUBS )
	set( smplayer2_LIBS
		${smplayer2_LIBS}
		${QUAZIP_LIBRARY}
	)
	set( smplayer2_HEADERS
		${smplayer2_HEADERS}
		findsubtitles/filedownloader/filedownloader.h
		findsubtitles/subchooserdialog.h
	)
	set( smplayer2_SOURCES
		${smplayer2_SOURCES}
		findsubtitles/filedownloader/filedownloader.cpp
		findsubtitles/subchooserdialog.cpp
	)
	set( smplayer2_FORMS
		${smplayer2_FORMS}
		findsubtitles/subchooserdialog.ui
	)
endif()

if( WIN32 )
	string( REPLACE "gcc" "windres" CMAKE_RC_COMPILER_INIT ${CMAKE_C_COMPILER} )
	enable_language( RC )
	set( CMAKE_RC_COMPILE_OBJECT
		"<CMAKE_RC_COMPILER> -O coff -o <OBJECT> <SOURCE>"
	)

	add_definitions( -DSCREENSAVER_OFF )
	add_definitions( -DUSE_ASSOCIATIONS )
	set( smplayer2_SOURCES
		${smplayer2_SOURCES}
		prefui/prefassociations.cpp
		screensaver.cpp
		smplayer2.rc
		winfileassoc.cpp
	)
	set( smplayer2_HEADERS
		${smplayer2_HEADERS}
		prefui/prefassociations.h
	)
	set( smplayer2_FORMS
		${smplayer2_FORMS}
		prefui/prefassociations.ui
	)
endif()

set( LINGUASINFO "\"All\", a space-seperated list of translations" )
set( LINGUASINFO "${LINGUASINFO} to install with SMPlayer2, or \"None\"." )

set( LINGUAS
	"All"
	CACHE STRING ${LINGUASINFO}
)
if( LINGUAS STREQUAL "All" )
	file( GLOB smplayer2_LANGUAGES translations/*.ts )
else()
	if( NOT LINGUAS OR LINGUAS STREQUAL "None" )
		set( smplayer2_LANGUAGES "" )
	else()
		string( REGEX MATCHALL [a-zA-Z_]+ langs ${LINGUAS} )
		foreach( lang ${langs} )
			list( APPEND langs translations/smplayer2_${lang}.ts )
		endforeach()
		file( GLOB smplayer2_LANGUAGES ${langs} )
	endif()
endif()

include_directories( ${CMAKE_CURRENT_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR} )

qt4_wrap_cpp( smplayer2_HEADERS_MOC ${smplayer2_HEADERS} )
qt4_wrap_ui( smplayer2_FORMS_HEADERS ${smplayer2_FORMS} )
qt4_add_translation( smplayer2_TRANSLATIONS ${smplayer2_LANGUAGES} )
qt4_add_resources( smplayer2_RESOURCES_RCC ${smplayer2_RESOURCES} )
add_custom_target( translations DEPENDS ${smplayer2_TRANSLATIONS} )

add_executable(smplayer2 WIN32
	${smplayer2_SOURCES}
	${smplayer2_HEADERS_MOC}
	${smplayer2_FORMS_HEADERS}
	${smplayer2_RESOURCES_RCC}
	# Next line only needed to show files in QtCreator source list
	${smplayer2_NOMOC_HEADERS}
)

add_dependencies( smplayer2 translations )
target_link_libraries( smplayer2 ${smplayer2_LIBS} )

install( TARGETS smplayer2 RUNTIME DESTINATION bin )
install(
	FILES ${smplayer2_TRANSLATIONS}
	DESTINATION share/smplayer2/translations
)

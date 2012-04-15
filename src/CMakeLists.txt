add_definitions("-DSMPLAYER2_VERSION=\"${SMPLAYER2_VERSION}\"")
if(NOT WIN32)
	add_definitions("-DDATA_PATH=\"${CMAKE_INSTALL_PREFIX}/share/smplayer2\"")
endif()

find_package(Qt4 REQUIRED QtCore QtGui QtNetwork QtXml)
find_package(ZLIB REQUIRED)
set(QT_USE_QTNETWORK TRUE)
set(QT_USE_QTXML TRUE)

include(${QT_USE_FILE})
add_definitions(${QT_DEFINITIONS})

set(smplayer2_gui_SOURCES
	gui/basegui.cpp
	gui/baseguiplus.cpp
	gui/defaultgui.cpp
	gui/minigui.cpp
	gui/mpcgui/mpcgui.cpp
	gui/mpcgui/mpcstyles.cpp
)

set(smplayer2_gui_HEADERS
	gui/basegui.h
	gui/baseguiplus.h
	gui/defaultgui.h
	gui/minigui.h
	gui/mpcgui/mpcgui.h
	gui/mpcgui/mpcstyles.h
)

set(smplayer2_prefui_SOURCES
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

set(smplayer2_prefui_HEADERS
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

set(smplayer2_prefui_FORMS
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


set(smplayer2_SOURCES
	about.cpp
	actionseditor.cpp
	assstyles.cpp
	audioequalizer.cpp
	clhelp.cpp
	colorutils.cpp
	core.cpp
	desktopinfo.cpp
	deviceinfo.cpp
	discname.cpp
	eqslider.cpp
	errordialog.cpp
	extensions.cpp
	favoriteeditor.cpp
	favorites.cpp
	filechooser.cpp
	filedialog.cpp
	filepropertiesdialog.cpp
	filesettings.cpp
	filesettingsbase.cpp
	filesettingshash.cpp
	filters.cpp
	findsubtitles/findsubtitlesconfigdialog.cpp
	findsubtitles/findsubtitleswindow.cpp
	findsubtitles/osparser.cpp
	findsubtitles/simplehttp.cpp
	floatingwidget.cpp
	global.cpp
	helper.cpp
	images.cpp
	infofile.cpp
	infoprovider.cpp
	inforeader.cpp
	inputdvddirectory.cpp
	inputurl.cpp
	languages.cpp
	lineedit_with_icon.cpp
	logwindow.cpp
	main.cpp
	mediadata.cpp
	mediasettings.cpp
	mplayerprocess.cpp
	mplayerwindow.cpp
	myaction.cpp
	myactiongroup.cpp
	myclient.cpp
	mycombobox.cpp
	mylineedit.cpp
	myprocess.cpp
	myserver.cpp
	myslider.cpp
	mytablewidget.cpp
	paths.cpp
	playlist.cpp
	playlistdock.cpp
	preferences.cpp
	prefwidget.cpp
	recents.cpp
	seekwidget.cpp
	selectcolorbutton.cpp
	shortcutgetter.cpp
	smplayer2.cpp
	subtracks.cpp
	timedialog.cpp
	timeslider.cpp
	titletracks.cpp
	toolbareditor.cpp
	tracks.cpp
	translator.cpp
	tristatecombo.cpp
	tvlist.cpp
	tvsettings.cpp
	urlhistory.cpp
	vdpauproperties.cpp
	verticaltext.cpp
	videoequalizer.cpp
	videopreview/videopreview.cpp
	videopreview/videopreviewconfigdialog.cpp
	widgetactions.cpp
	${smplayer2_gui_SOURCES}
	${smplayer2_prefui_SOURCES}
)

set(smplayer2_HEADERS
	about.h
	actionseditor.h
	audioequalizer.h
	core.h
	eqslider.h
	errordialog.h
	favoriteeditor.h
	favorites.h
	filechooser.h
	filepropertiesdialog.h
	filters.h
	findsubtitles/findsubtitlesconfigdialog.h
	findsubtitles/findsubtitleswindow.h
	findsubtitles/simplehttp.h
	floatingwidget.h
	inforeader.h
	inputdvddirectory.h
	inputurl.h
	languages.h
	lineedit_with_icon.h
	logwindow.h
	mplayerprocess.h
	mplayerwindow.h
	myactiongroup.h
	mylineedit.h
	myprocess.h
	myserver.h
	myslider.h
	playlist.h
	playlistdock.h
	seekwidget.h
	selectcolorbutton.h
	shortcutgetter.h
	timedialog.h
	timeslider.h
	tristatecombo.h
	tvlist.h
	vdpauproperties.h
	videoequalizer.h
	videopreview/videopreview.h
	videopreview/videopreviewconfigdialog.h
	widgetactions.h
	${smplayer2_gui_HEADERS}
	${smplayer2_prefui_HEADERS}
)

set(smplayer2_FORMS
	about.ui
	eqslider.ui
	errordialog.ui
	favoriteeditor.ui
	filepropertiesdialog.ui
	findsubtitles/findsubtitlesconfigdialog.ui
	findsubtitles/findsubtitleswindow.ui
	inputdvddirectory.ui
	inputurl.ui
	logwindowbase.ui
	seekwidget.ui
	timedialog.ui
	vdpauproperties.ui
	videopreview/videopreviewconfigdialog.ui
	${smplayer2_prefui_FORMS}
)

set(smplayer2_OTHER_HEADERS
	gui/guiconfig.h
	preferences.h
)

set(smplayer2_RESOURCES icons.qrc)
set(smplayer2_LIBS ${QT_LIBRARIES} ${ZLIB_LIBRARY})

if(HAVE_DOWNLOAD_SUBS)
	add_definitions(-DDOWNLOAD_SUBS)
	set(smplayer2_LIBS ${smplayer2_LIBS} ${QUAZIP_LIBRARY})
	set(smplayer2_HEADERS ${smplayer2_HEADERS}
		findsubtitles/filedownloader/filedownloader.h
		findsubtitles/subchooserdialog.h)
	set(smplayer2_SOURCES ${smplayer2_SOURCES}
		findsubtitles/filedownloader/filedownloader.cpp
		findsubtitles/subchooserdialog.cpp)
	set(smplayer2_FORMS ${smplayer2_FORMS}
		findsubtitles/subchooserdialog.ui)
endif()

if(WIN32)
	string(REPLACE "gcc" "windres" CMAKE_RC_COMPILER_INIT ${CMAKE_C_COMPILER})
	enable_language(RC)
	set(CMAKE_RC_COMPILE_OBJECT "<CMAKE_RC_COMPILER> -O coff -o <OBJECT> <SOURCE>")

	add_definitions(-DSCREENSAVER_OFF)
	add_definitions(-DUSE_ASSOCIATIONS)
	set(smplayer2_SOURCES ${smplayer2_SOURCES}
	screensaver.cpp
	prefui/prefassociations.cpp
	winfileassoc.cpp
	smplayer2.rc
	)
	set(smplayer2_HEADERS ${smplayer2_HEADERS}
	prefui/prefassociations.h
	)
	set(smplayer2_FORMS ${smplayer2_FORMS}
	prefui/prefassociations.ui
	)
endif()

set(LINGUAS "All" CACHE STRING "\"All\", a space-seperated list of translations to install with SMPlayer2, or \"None\".")
if (LINGUAS STREQUAL "All")
	file(GLOB smplayer2_LANGUAGES translations/*.ts)
else ()
if (NOT LINGUAS OR LINGUAS STREQUAL "None")
	set (smplayer2_LANGUAGES "")
else ()
	string(REGEX MATCHALL [a-zA-Z_]+
			langs ${LINGUAS})
	foreach(lang ${langs})
		list(APPEND langs translations/smplayer2_${lang}.ts)
	endforeach()
	file(GLOB smplayer2_LANGUAGES ${langs})
endif ()
endif ()

qt4_wrap_cpp(smplayer2_HEADERS_MOC ${smplayer2_HEADERS})
qt4_wrap_ui(smplayer2_FORMS_HEADERS ${smplayer2_FORMS})
qt4_add_translation(smplayer2_TRANSLATIONS ${smplayer2_LANGUAGES})
qt4_add_resources(smplayer2_RESOURCES_RCC ${smplayer2_RESOURCES})
add_custom_target(translations DEPENDS ${smplayer2_TRANSLATIONS})

add_executable(smplayer2 WIN32
	${smplayer2_SOURCES}
	${smplayer2_HEADERS_MOC}
	${smplayer2_FORMS_HEADERS}
	${smplayer2_RESOURCES_RCC}
	${smplayer2_OTHER_HEADERS}
)

add_dependencies(smplayer2 translations)
target_link_libraries(smplayer2 ${smplayer2_LIBS})
include_directories(${CMAKE_CURRENT_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR})

install(TARGETS smplayer2 RUNTIME DESTINATION bin)
install(FILES ${smplayer2_TRANSLATIONS} DESTINATION share/smplayer2/translations)

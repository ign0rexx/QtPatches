These patches were tested with MSVC 2019 using the v141_xp toolchain.

Static build
------------

The optional static-link.patch is recommended for static builds. It allows to link
the C++ runtime statically producing self-contained executables that don't require
installing "Visual Studio Redistributables".

```
configure -platform win32-msvc -static -static-runtime -debug-and-release -no-pch -nomake tests -nomake examples -skip qt3d -skip qtactiveqt -skip qtconnectivity -skip qtdatavis3d -skip qtdeclarative -skip qtlocation -skip qtlottie -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquick3d -skip qtquickcontrols -skip qtquickcontrols2 -skip qtquicktimeline -skip qtremoteobjects -skip qtsensors -skip qtvirtualkeyboard -skip qtwebchannel -skip qtwebengine -skip qtwebglplugin -skip qtwebsockets -skip qtwebview -no-sql-odbc -no-sql-sqlite -opensource -confirm-license
```

Shared build
------------

Apply subsystem-version.patch so that compiled .dll and .exe files have a minimum
version of 5.01, allowing them to run on XP.

```
configure -platform win32-msvc -shared -debug-and-release -no-pch -nomake tests -nomake examples -skip qt3d -skip qtactiveqt -skip qtconnectivity -skip qtdatavis3d -skip qtdeclarative -skip qtlocation -skip qtlottie -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquick3d -skip qtquickcontrols -skip qtquickcontrols2 -skip qtquicktimeline -skip qtremoteobjects -skip qtsensors -skip qtvirtualkeyboard -skip qtwebchannel -skip qtwebengine -skip qtwebglplugin -skip qtwebsockets -skip qtwebview -no-sql-odbc -no-sql-sqlite -opensource -confirm-license
```

What doesn't work
-----------------

Chromium aka QtWebEngine is not supported. All QtDeclarative/QML stuff is currently
excluded from the build, though it should theoretically work via ANGLE and Direct3D 9.0.

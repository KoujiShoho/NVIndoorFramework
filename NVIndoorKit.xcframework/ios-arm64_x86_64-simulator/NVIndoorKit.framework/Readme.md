#  BUILD DEVICE

xcodebuild archive \
-workspace NVIndoorKit.xcworkspace \
-scheme NVIndoorKit \
-configuration Release \
-sdk iphoneos \
-archivePath archives/NVIndoorKit-iphoneos.xcarchive \
BUILD_LIBRARY_FOR_DISTRIBUTION=YES \
SKIP_INSTALL=NO \

#  BUILD SIMULATOR

xcodebuild archive \
-workspace NVIndoorKit.xcworkspace \
-scheme NVIndoorKit \
-configuration Release \
-sdk iphonesimulator \
-archivePath archives/NVIndoorKit-iphonesimulator.xcarchive \
BUILD_LIBRARY_FOR_DISTRIBUTION=YES \
SKIP_INSTALL=NO \

#  BUILD XCFRAMEWORK

xcodebuild -create-xcframework \
-framework 'archives/NVIndoorKit-iphonesimulator.xcarchive/Products/Library/Frameworks/NVIndoorKit.framework' \
-framework 'archives/NVIndoorKit-iphoneos.xcarchive/Products/Library/Frameworks/NVIndoorKit.framework' \
-output 'archives/NVIndoorKit.xcframework'

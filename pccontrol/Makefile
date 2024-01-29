#export THEOS_DEVICE_IP = 192.168.0.6
TARGET := iphone:clang:latest:14.5
include $(THEOS)/makefiles/common.mk

TWEAK_NAME = pccontrol

pccontrol_FILES = Tweak.xm SocketServer.xm Touch.xm Screen.xm Task.xm Process.xm AlertBox.xm Common.xm Record.xm Play.xm Window.xm Popup.xm TemplateMatch.xm ScreenMatch.xm Toast.xm Image.xm ColorPicker.xm UIKeyboard.xm DeviceInfo.xm TouchIndicator/TouchIndicatorWindow.xm TouchIndicator/TouchIndicatorView.xm TouchIndicator/TouchIndicatorCoordinateView.xm TouchIndicator/TouchIndicatorViewList.xm ScriptPlayer.xm Activator/ActivatorListener.xm TextRecognization/VKOcrManager.xm TextRecognization/TextRecognizer.xm UpdateCache.xm
pccontrol_CFLAGS = -DENABLE_NEON=ON -Wno-error -Wno-module-import-in-extern-c -fobjc-arc
pccontrol_FRAMEWORKS = UIKit opencv2 AssetsLibrary AVFoundation CoreMedia CoreVideo IOSurface
#pccontrol_LDFLAGS += -L./libs/IOMobileFramebuffer.framework/IOMobileFramebuffer
# link libjpeg.a
#pccontrol_LDFLAGS += -L./libjpeg.a
pccontrol_ARCHS =  arm64 arm64e
#pccontrol_CCFLAGS = -std=c++11
#使用3.1.0版本编译错误只有一个
pccontrol_PRIVATE_FRAMEWORKS = IOKit
pccontrol_LIBRARIES = substrate

include $(THEOS_MAKE_PATH)/tweak.mk

after-install::
	install.exec "chown -R mobile:mobile /var/mobile/Library/ZXTouch && killall -9 SpringBoard;"



# kded_rotation

KDED module for handling automatic screen rotation on X11, with visual feedback before orientation change happens. Some assembly might be required.

# Installation
Install dependences:
- On Fedora:
```
dnf -y install qt5-qtbase-devel cmake extra-cmake-modules iio-sensor-proxy xrandr qt5-qtsensors kf5-kded-devel xinput qt5-qtsensors-devel qt5-qtbase-devel kf5-kcoreaddons-devel kf5-kdbusaddons-devel kf5-kded-devel
```
Run `./install_kded_rotation.sh`. 

# Usage

`orientation-helper` is where the actual screen rotation happens. This is achieved by calling `xrandr --rotation $value`, which works in most circumstances. You can adjust `orientation-helper` to fit your setup and reinstall to apply.

To reduce or increase the timer before the rotation happens, adjust `timer.start(25);` in `screenrotator.cpp`:

```cpp
void ScreenRotator::startProgress() {
	if (progress == -1) {
		timer.start(25);
		progress = 0;
	}
}
```

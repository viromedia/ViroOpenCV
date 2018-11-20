# Building for Android

1. CD into the OpenCV directory and create a build directory
```
cd opencv-3.4.3
mkdir android-build
cd android-build
```

2. Run CMake

```
cmake .. -DCMAKE_SYSTEM_NAME=Android -DCMAKE_SYSTEM_VERSION=[ANDROID VERSION] -DCMAKE_ANDROID_ARCH_ABI=[ARCH] -DCMAKE_ANDROID_NDK=[NDK_PATH] -DCMAKE_ANDROID_STL_TYPE=gnustl_static -DCMAKE_INSTALL_PREFIX=android-build
```
where:

[ARCH] is either ```armeabi-v7a``` or ```arm64-v8a```
[NDK_PATH] points to your NDK installation (for me: /Users/radvani/Library/Android/sdk/ndk-bundle )
[VERSION] indicates the android version (in general we've been using 21)

Filled in, it would look something like this
```
cmake .. -DCMAKE_SYSTEM_NAME=Android -DCMAKE_SYSTEM_VERSION=28 -DCMAKE_ANDROID_ARCH_ABI=arm64-v8a -DCMAKE_ANDROID_NDK=/Users/radvani/Library/Android/sdk/ndk-bundle -DCMAKE_ANDROID_STL_TYPE=gnustl_static -DCMAKE_INSTALL_PREFIX=android-build
```

3. Follow steps 4 through 6 in Alternative A


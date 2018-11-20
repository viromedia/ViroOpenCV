# Building for Android

1. CD into the OpenCV directory and create a build directory
```
cd opencv-3.4.3
mkdir android-build
cd android-build
```

2. Run CMake

```
cmake -GNinja -DINSTALL_ANDROID_EXAMPLES=OFF -DANDROID_EXAMPLES_WITH_LIBS=OFF -DBUILD_EXAMPLES=OFF -DBUILD_DOCS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_TESTS=OFF -DWITH_OPENCL=OFF -DWITH_TBB=ON -DCMAKE_TOOLCHAIN_FILE={NDK_PATH}/build/cmake/android.toolchain.cmake -DANDROID_TOOLCHAIN=clang -DANDROID_STL=c++_static -DANDROID_SDK_TARGET={VERSION} -DBUILD_ANDROID_PROJECTS=ON -DANDROID_ABI={ARCH} -DANDROID_ARM_NEON=ON -DANDROID_PROJECTS_BUILD_TYPE=ANT ..
```
where:

{ARCH} can be either  ```armeabi-v7a``` or ```arm64-v8a```
{NDK_PATH} points to your NDK installation (for me: /Users/radvani/Library/Android/sdk/ndk-bundle )
{VERSION} indicates the android version (in general we've been using 21)

Filled in, it would look something like this
```
cmake -GNinja -DINSTALL_ANDROID_EXAMPLES=OFF -DANDROID_EXAMPLES_WITH_LIBS=OFF -DBUILD_EXAMPLES=OFF -DBUILD_DOCS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_TESTS=OFF -DWITH_OPENCL=OFF -DWITH_TBB=ON -DCMAKE_TOOLCHAIN_FILE=~/Library/Android/sdk/ndk-bundle/build/cmake/android.toolchain.cmake -DANDROID_TOOLCHAIN=clang -DANDROID_STL=c++_static -DANDROID_SDK_TARGET=21 -DBUILD_ANDROID_PROJECTS=ON -DANDROID_ABI=arm64-v8a -DANDROID_ARM_NEON=ON -DANDROID_PROJECTS_BUILD_TYPE=ANT ..
```

3. Build
```
ninja -j8
ninja install
```

4. The libs will be in the android_build/lib and android_build/3rdparty/lib folders

### IMPORTANT: Between building architectures, delete the entire android_build directory


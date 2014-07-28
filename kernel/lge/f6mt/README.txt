1. Android build
  - Download original android source code ( KitKat 4.4.2 ) from http://source.android.com
  - Untar opensource packages of LG-D505_F6_Android_KK_D50520a_Android.tar.gz* into downloaded android source directory 
    $ cat LG-D505_F6_Android_KK_D50520a_Android.tar.gz* | tar xvzf -
  - And, merge the source into the android source code(KitKat)
  - Replace vendor folder to other space
  - Run following scripts to build android
    $ source ./build/envsetup.sh
    $ choosecombo 1 generic user
    $ make -j4
  - When you compile the android source code, you have to add google original prebuilt source(toolchain)
    into the android folder
  - After build, you can find output at out/target/product/generic
  - move back vendor to where it was and follow README inside vendor to apply rest of them

2. Kernel Build
  - Uncompress using following command at the android directory
    $ tar -xvzf LGD505_F6_Android_KK_D50520a_Kernel.tar.gz
  - Build kernel
    $ cd kernel
    $ make f6_nfc_defconfig  ARCH=arm CROSS_COMPILE=arm-eabi-
    $ make ARCH=arm CROSS_COMPILE=arm-eabi- -j4
  - After Build, You Can find the build image at arch/arm/boot

3. how  to build chromium_lge (vendor\lge\external\chromium_lge\src),
   please refer to README.txt at the folder mentioned above.
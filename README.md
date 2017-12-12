#download source

repo init -u git://github.com/LineageOS/android.git -b cm-14.1

mkdir .repo/local_manifests

copy ${PATH_TO}/d838.xml .repo/local_manifests/

repo sync

#apply patches

copy ${PATH_TO}/framework_av.patch frameworks/av/

cd frameworks/av/

git apply framework_av.patch

cd -

copy ${PATH_TO}/framework_native.patch frameworks/native/

cd frameworks/native/

git apply framework_native.patch

cd -

#build

. build/envsetup.sh

breakfast d838

make bacon -j8

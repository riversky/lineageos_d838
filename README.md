# download source

repo init -u git://github.com/LineageOS/android.git -b cm-14.1

mkdir .repo/local_manifests

copy ${PATH_TO}/d838.xml .repo/local_manifests/

repo sync

# build

. build/envsetup.sh

breakfast d838

make bacon -j8

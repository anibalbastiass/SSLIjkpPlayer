# SSLIjkpPlayer
IjskPlayer + Open SSL for Android (Video Android Player) by @anibalbastiass

For use in Android, add in app/build.gradle

```gradle
// Ijkplayer + openSSL video player (FFMPEG)
implementation 'com.google.android.exoplayer:exoplayer:2.9.1'
implementation 'com.github.anibalbastiass:SSLIjkpPlayer:1.0.1'

// Video Player
implementation 'cn.jzvd:jiaozivideoplayer:7.0.3'
```
## How I build this lib?

First of all, clone ijkplayer repo
`$ git clone https://github.com/Bilibili/ijkplayer.git`

1. Change config/module.sh with module-lite.sh

```
$ cd config
$ rm module.sh
$ ln -s module-lite.sh module.sh
```

2. init openssl

```
$ cd ..
$ ./init-android-openssl.sh
```

3. compile openssl

```
$ cd android/contrib
$ ./compile-openssl.sh clean
$ ./compile-openssl.sh all
```

4. init android

```
$ cd ../..
./init-android.sh
```

5. compile ffmpeg (x86_64 need yasm: $ brew install yasm)

```
$ cd android/contrib
$ ./compile-ffmpeg.sh clean
$ ./compile-ffmpeg.sh all
```

6. compile ijk

```
$ cd ..
$ ./compile-ijk.sh all
```

7. copy so files

```
cp ijkplayer/ijkplayer-armv5/src/main/libs  ijkplayer-java/src/main/jniLibs
cp ijkplayer/ijkplayer-armv7a/src/main/libs  ijkplayer-java/src/main/jniLibs
cp ijkplayer/ijkplayer-arm64/src/main/libs  ijkplayer-java/src/main/jniLibs
cp ijkplayer/ijkplayer-x86/src/main/libs ijkplayer-java/src/main/jniLibs
```

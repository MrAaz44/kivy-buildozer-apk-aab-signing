# kivy-buildozer-apk-aab-signing
> This repo explain to how sign your aab or apk on google colab

> 1 - open the colab https://colab.research.google.com

> 2 - install the requier package:
```
!pip install buildozer
!pip install cython==0.29.19
!lsb_release -a
!sudo apt-get install -y \
    python3-pip \
    build-essential \
    git \
    python3 \
    python3-dev \
    ffmpeg \
    libsdl2-dev \
    libsdl2-image-dev \
    libsdl2-mixer-dev \
    libsdl2-ttf-dev \
    libportmidi-dev \
    libswscale-dev \
    libavformat-dev \
    libavcodec-dev \
    zlib1g-dev
!sudo apt-get install -y \
    libgstreamer1.0 \
    gstreamer1.0-plugins-base \
    gstreamer1.0-plugins-good
!sudo apt-get install build-essential libsqlite3-dev sqlite3 bzip2 libbz2-dev zlib1g-dev libssl-dev openssl libgdbm-dev libgdbm-compat-dev liblzma-dev libreadline-dev libncursesw5-dev libffi-dev uuid-dev libffi6
!sudo apt-get install libffi-dev
!sudo apt install libtool
!sudo apt-get install automake
!sudo apt-get install autoconf
!sudo apt-get install libltdl-dev
!sudo apt install automake
```
> and if you are signing a aab file add this but if it is apk don't add.

```
!pip install https://github.com/misl6/buildozer/archive/refs/heads/feat/aab-support.zip
```

> after that 

```
!mkdir keystores
```

> in this part you need a define a key name to <your-new-key> and a alias to <your-key-alias> and a password to after and never forgot this and write it the after parts to <your-new-key> and the others.

```
!keytool -genkey -v -keystore /content/keystores/<your-new-key>.keystore -alias <your-key-alias> -keyalg RSA -keysize 2048 -validity 10000
```
```
!keytool -importkeystore -srckeystore /content/keystores/<your-new-key>.keystore -destkeystore /content/keystores/<your-new-key>.keystore -deststoretype pkcs12
```
```
%env P4A_RELEASE_KEYSTORE=/content/keystores/<your-new-key>.keystore
%env P4A_RELEASE_KEYSTORE_PASSWD=android
%env P4A_RELEASE_KEYALIAS_PASSWD=android
%env P4A_RELEASE_KEYALIAS=<your-key-alias>
```
	
> And after this you can check with !export and see your keystore things
  
> When you are signing it will ask some question like where are u from you can just past them (enter).execpt password you have to write it.Write your password 2.%env and 3.%env.

  
> After this you can write !buildozer init and spec file is come.You have to change your package domain.And not necessasry but change title and the package.name
  
> If you are signing aab file you have to change p4a.branch = develop and android.release.artifact = aab
> Finally:
!buildozer -v android release or !buildozer -v android debug(I recommend the first)
  
> If you have a question you can write me on discord: MrAaz#0359

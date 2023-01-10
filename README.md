# Mobile Security Framework(MobSF) Snap
**Mobile Security Framework (MobSF)** is an automated, all-in-one mobile application(Android/iOS/Windows) pen-testing, malware analysis and security assessment framework capable of performing static and dynamic analysis. MobSF supports mobile app binaries (APK, XAPK, IPA & APPX) along with zipped source code and provides REST APIs for seamless integration with your CI/CD or DevSecOps pipeline.The Dynamic Analyzer helps you to perform runtime security assessment and interactive instrumented testing.

**MobSF** is created and currently maintained by [@ajinabraham](https://github.com/ajinabraham). [MobSF snap](https://snapcraft.io/mobsf) is possible only because of the awesome work of [@ajinabraham](https://github.com/ajinabraham) and the [contributors](https://github.com/MobSF/Mobile-Security-Framework-MobSF/graphs/contributors) of [MobSF project](https://github.com/MobSF/Mobile-Security-Framework-MobSF) and all the credit goes to them.

This is the best snap I've created so far. During my testing, this snap worked so well that I felt like I'm using some commercial grade app and not an Open Source project. :) Given the ease of installation and usage, I can say that even non-technical users can use it easily. I hope people will report bugs.

Happy Hacking! 

<br></br>
## Installation and Usage

### Installation

To install MobSF snap, use the following command:-
```bash
snap install mobsf
```


### Usage
To run MobSF, use the following command:-
```bash
mobsf
````
By default MobSF will listen on localhost port **8000** and you can browse to `http://127.0.0.1:8000` in you browser to start it. If you want to use a custom port, then use the following command:-
```bash
mobsf <ip>:<port>
```
![image](https://user-images.githubusercontent.com/83544797/211560322-d29e45bf-2421-48fd-bb4a-dd3a1acdc959.png)
> **Note:-** The **first time** you run MobSF, it will produce a lot of output which is normal and expected. MobSF has to create the necessary configurations, database and its contents etc. during its first run and the user should wait for it to finish.  

&nbsp;

## Dynamic Analyzer

### Genymotion and Android Studio

MobSF snap recognizes running **Genymotion Android VMs** and **Android Studio Emulator AVDs** out of the box. But, as the AVDs started inside **Android Studio** are not run with writable `/system` folder, MobSF cannot upload the `frida-server` binary to the AVDs `/system` folder to **MobSFy** it. You can follow [MobSF official documentation](https://mobsf.github.io/docs/#/dynamic_analyzer?id=android-studio-emulator) on how start an Android Studio AVD with a **writable system**. Also, MobSF snap ships its own `adb` binary and is preconfigured to use it and is expected to work well with it, so you shouldn't change it unless really necessary. In the rare case you do need to use your own `adb` binary, then you can change the `ADB_BINARY` variable in `~/snap/mobsf/current/.MobSF/config.py` and change the binary path to your own.
> **Note:-** This snap doesn't have read access to many locations outside your $HOME folder and also can't read files inside **hidden folders**(folders starting with a `.`) as some user-related *sensitive* config files are stored there. So make sure your `ADB_BINARY` path is both inside your $HOME folder and not in a hidden folder.

### Virtual Machines
Although not mentioned in [MobSF official docs](https://mobsf.github.io/docs), MobSF Dynamic Analyzer works just fine inside **Virtual Machines**. I've tested **MobSF snap** inside a **VM** and it worked without any problems. You're welcome to try it in a **VM**, but remember, DON'T report bugs in this repo or in the official repo if you decided to install MobSF inside a **Virtual Machine** and are facing issues with it! You're on your own if you decided to run it inside a **VM**!
![image](https://user-images.githubusercontent.com/83544797/211560214-0b374359-3bf2-45ea-b7c2-d1f6026108c8.png)

### Cloud Android
I've not tested Cloud VMs with MobSF snap, but those should work too if you follow the [MobSF official guide](https://mobsf.github.io/docs/#/dynamic_analyzer?id=genymotion-cloud-android). You can use the system `adb` binary to connect to the Android Cloud VM and MobSF snap will detect it automatically. In case you need to use the snap's builtin `adb` binary to connect to the Android Cloud VM, then you can use **shell** inside the MobSF snap to use the `adb` binary with the following command:-
```bash
snap run --shell mobsf
```
![image](https://user-images.githubusercontent.com/83544797/211560076-f563e934-d2a8-4d6a-95ea-57d0109a4022.png)

### Physical Devices
MobSF snap also works with physical devices, but as it is **not officially supported**, DON't report bugs about snap usage with physical devices in this repo too! For the curious who want to try out, you can use a Android device with **root** access, because as mentioned before MobSF needs write access to device's `/system` folder. 

<br></br>
***
## About this repo
This repo provides the necessary files to create a snap package for [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF). It'll work on Debian, Fedora, Ubuntu and all other major Linux distributions that have [snapd](https://snapcraft.io/docs/installing-snapd) installed.

Official Docs:- https://mobsf.github.io/docs

<br></br>

&nbsp;





***
**Snap created for Linux** ~~with love~~ with a keyboard **by Jitendra Patro.**


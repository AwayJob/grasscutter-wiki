# Prerequisites
- [MongoDB](https://www.mongodb.com/try/download/community), [MongoDB Tutorial](https://github.com/Grasscutters/Grasscutter/wiki/Resources#mongodb-tutorial)
- [JDK 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)

# Starting the Server
**If you haven't already, download `grasscutter.jar` from [actions](https://github.com/Grasscutters/Grasscutter/releases)/[Jenkins](https://jenkins.4benj.com/job/Grasscutters/job/Grasscutter/lastSuccessfulBuild/) or [build the server by yourself](https://github.com/Grasscutters/Grasscutter/wiki/Building)**.

1. Run `java -jar grasscutter.jar`
   - This will create additional directories in your working directory.
2. Copy the following files to the following directories: (file source -> `destination`)
   - [yukiz](https://gitlab.com/yukiz/GrasscutterResources/) or [Koko-boya](https://github.com/Koko-boya/Grasscutter_Resources) -> `resources`
   - [The Keystore File](https://github.com/Grasscutters/Grasscutter/blob/main/keystore.p12) -> `keystore.p12`
   - **Note**: If you are running in the project's root directory (ie. you cloned the repo from GitHub and you are running the server in that folder), these files will be already be present.
3. Run `java -jar grasscutter.jar -handbook`
   - This is required for using `names -> IDs` in commands.
   - This setup is optional and can be skipped.
4. Make sure to setup your operating system firewall settings
   - Windows: Make sure to allow their port on Windows Firewall Settings (80, 443, 8888, and 22102)
   - Linux: Make sure to write `sudo ufw allow 22102`, `sudo ufw allow 443`, `sudo ufw allow 80`, and `sudo ufw allow 8888` .
4. Run `java -jar grasscutter.jar`
   1. (kinda obvious but) Leave this running in the background.
5. Continue to [Connecting](#connecting)

# Connecting
**Note**: This works for connecting to external servers as well.

## Prerequisites
- [mitmproxy](https://mitmproxy.org/), [Fiddler Classic](https://telerik-fiddler.s3.amazonaws.com/fiddler/FiddlerSetup.exe), [Hosts file](https://github.com/Grasscutters/Grasscutter/wiki/Resources#hosts-file) (or another proxy to redirect web traffic)

1. Run your choosen web traffic proxy.
2. Route all traffic going to HoYoVerse/MiHoYo servers using [mitmproxy](https://github.com/Grasscutters/Grasscutter#:~:text=mitmdump:), [Fiddler](https://github.com/Grasscutters/Grasscutter#:~:text=Fiddler%20Classic:) or [Hosts file](https://github.com/Grasscutters/Grasscutter/wiki/Resources#hosts-file) to the server host.
3. Launch Genshin Impact and have fun!

## [Traffic Route Map](https://github.com/Grasscutters/Grasscutter/issues/1447)
```
dispatchosglobal.yuanshen.com -> (redirect to the server host)
dispatchcnglobal.yuanshen.com -> (redirect to the server host)
osusadispatch.yuanshen.com -> (redirect to the server host)
oseurodispatch.yuanshen.com -> (redirect to the server host)
osasiadispatch.yuanshen.com -> (redirect to the server host)

hk4e-api-os-static.mihoyo.com -> (redirect to the server host)
hk4e-api-static.mihoyo.com -> (redirect to the server host)
hk4e-api-os.mihoyo.com -> (redirect to the server host)
hk4e-api.mihoyo.com -> (redirect to the server host)
hk4e-sdk-os.mihoyo.com -> (redirect to the server host)
hk4e-sdk.mihoyo.com -> (redirect to the server host)

account.mihoyo.com -> (redirect to the server host)
api-os-takumi.mihoyo.com -> (redirect to the server host)
api-takumi.mihoyo.com -> (redirect to the server host)
sdk-os-static.mihoyo.com -> (redirect to the server host)
sdk-static.mihoyo.com -> (redirect to the server host)
webstatic-sea.mihoyo.com -> (redirect to the server host)
webstatic.mihoyo.com -> (redirect to the server host)
uploadstatic-sea.mihoyo.com -> (redirect to the server host)
uploadstatic.mihoyo.com -> (redirect to the server host)

api-os-takumi.hoyoverse.com -> (redirect to the server host)
sdk-os-static.hoyoverse.com -> (redirect to the server host)
sdk-os.hoyoverse.com -> (redirect to the server host)
webstatic-sea.hoyoverse.com -> (redirect to the server host)
uploadstatic-sea.hoyoverse.com -> (redirect to the server host)
api-takumi.hoyoverse.com -> (redirect to the server host)
sdk-static.hoyoverse.com -> (redirect to the server host)
sdk.hoyoverse.com -> (redirect to the server host)
webstatic.hoyoverse.com -> (redirect to the server host)
uploadstatic.hoyoverse.com -> (redirect to the server host)
account.hoyoverse.com -> (redirect to the server host)
api-account-os.hoyoverse.com -> (redirect to the server host)
api-account.hoyoverse.com -> (redirect to the server host)

hk4e-api-os.hoyoverse.com -> (redirect to the server host)
hk4e-api-os-static.hoyoverse.com -> (redirect to the server host)
hk4e-sdk-os.hoyoverse.com -> (redirect to the server host)
hk4e-sdk-os-static.hoyoverse.com -> (redirect to the server host)
hk4e-api.hoyoverse.com -> (redirect to the server host)
hk4e-api-static.hoyoverse.com -> (redirect to the server host)
hk4e-sdk.hoyoverse.com -> (redirect to the server host)
hk4e-sdk-static.hoyoverse.com -> (redirect to the server host)

log-upload.mihoyo.com -> (redirect to 0.0.0.0)
log-upload-os.mihoyo.com -> (redirect to 0.0.0.0)
log-upload-os.hoyoverse.com -> (redirect to 0.0.0.0)
devlog-upload.mihoyo.com -> (redirect to 0.0.0.0)
overseauspider.yuanshen.com -> (redirect to 0.0.0.0)
```

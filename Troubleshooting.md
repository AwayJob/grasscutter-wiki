> Ctrl + F is your friend :)

> Thanks to Thoronium and others for the solutions.

# Build Errors
 
## Gradle: Could not initialize class...

**Error Example:**
![lol](https://media.discordapp.net/attachments/965284036333424722/965743823445696552/11.png)

**Potential places for error**:
- Gradle is using the wrong version of Java/the JDK.

**Solution**:
- Specify the correct version using:
```cmd
set %JAVA_HOME%=C:\Program Files\Java\jdk-XX.X.X.X
``` 

# Server Console Errors
 
## ...not recognized as an internal or external command. 
 
**Potential places for error**:
- You don't have java in your PATH.

**Solutions**:
- Make sure you have [java](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) installed and [add it to PATH manually](https://www.java.com/en/download/help/path.html).
 
## [Dispatch] No SSL cert found! Falling back to HTTP server. 

**Potential places for error**:
- No SSL cert, you're missing essential files from the repository.

**Solutions**:
- Download `keystore.p12` in the [repository](https://github.com/Grasscutters/Grasscutter) properly. 


## Address already in use: bind, java.net.BindException
This error is derived from the server being unable to bind to a certain port.
The server uses ports: `80`, `443`, `8888`, and `22102` (by default)
 
**Potential places for error**:
- The dispatch (web/HTTP[S]) server has double-bounded.
- One of the above ports (or any you've specified) has been bound to by another process.
- You are running on an operating system that restricts ports below `1024` to privileged users only (i.e. not Windows).
 
**Solutions**:
- If an SSL certificate error is logged to the console, check your `keystore.p12` is in the correct place and with the correct password.
- Run `netstat -aon | find /i "listening"` to find processes with the server ports. Then kill the process with `taskkill /PID <PID>`.
- Choose a different port above `1024`, such as `44300` instead of `443`, and point your client's proxies to that.
 
 
## Unable to access jarfile.
 
**Potential places for error**:
- You either are not using the right file name in your command. 
- Not running the command from your grasscutter folder. 
- Most likely your built jar is broken. 
 
**Solutions**:
- Use the correct file name instead of `grasscutter.jar`.
- Locate your grasscutter folder and open the command prompt there or navigate using the command `cd` to your grasscutter folder. 
- Build grasscutter first with `gradlew jar`. Make sure to follow the installation instructions in the [README](https://github.com/Grasscutters/Grasscutter#building)/[Wiki](https://github.com/Grasscutters/Grasscutter/wiki/Building) properly or download the `grasscutter.jar` from [actions](https://github.com/Grasscutters/Grasscutter/actions/workflows/build.yml)/[4benj](https://jenkins.4benj.com/job/Grasscutters/job/Grasscutter/lastSuccessfulBuild/). 
 
 
## MongoSocketOpenException, Connection refused, Exception opening socket, ECONNREFUSED
 
**Potential places for error**:
- MongoDB is not running. 
 
**Solutions**:
- Start `mongod.exe` in `C:\Program Files\MongoDB\Server\<version>\bin`


## <ERROR:ResourceLoader> Error loading resource file: [...] java.io.FileNotFoundException: .\resources\... (The system cannot find the path specified)

**Potential places for error**:
- You are missing resources.

**Solutions**:
- Download the latest resources from [yukiz](https://gitlab.com/yukiz/GrasscutterResources/) or [tamilpp25](https://github.com/tamilpp25/Grasscutter_Resources).
- Make sure the path to your resources is like this:
```
.\grasscutter\resources\BinOutput, ExcelBinOutput etc.
```

## Cannot invoke "emu.grasscutter.game.home.HomeSceneItem.getRoomSceneID()" because "homeScene" is null

**Potential places for error**:
- You went into the teapot.

**Solutions**:
- Your account is softlocked, make a new one.
- You could try editing `homeroomscene` in mongodb but if you go into teapot again it will softlock.

# Client Errors

## Server busy. Please try again later.(502)

**Potential places for error**:
- Cetificate Issue/You didn't installed the certificate. 
- Server not started right/not accessible/not configured correctly if Fiddler is set up correctly.
- No SSL cert, you're missing essential files from the repository.

**Solutions**:
- In Fiddler, go to `Tools Tab -> Options -> HTTPS Tab -> Actions Button -> Trust Root Certificate`.
- Download `keystore.p12` in the [repository](https://github.com/Grasscutters/Grasscutter) properly. 


## Error Code: 4201
 
**Potential places for error**:
- Proxy is not connected successfully.
 
**Solutions**:
- Check your Proxy Daemon, whether if it is running/working.
 
 
## Error Code: 4206
 
**Potential places for error**:
- The server's ports are blocked by a firewall:
  - Your operating system firewall is blocking one or more Grasscutter ports.
  - Your VPS host's firewall is blocking one or more Grasscutter ports.
- The server has not configured HTTPS correctly.
 
**Solutions**:
- Check your firewall settings:
  - Windows: Allow the ports on Windows Firewall settings (`80`, `443`, `8888`, and `22102`)
  - Linux: Run `sudo ufw allow 80`, `sudo ufw allow 443`, `sudo ufw allow 8888`, and `sudo ufw allow 22102`.
  - Check your hosting panel (e.g. Azure or Google Cloud), find the networking or firewall setting on the panel, and allow the following ports:<br/>
Allowed ports: `80`, `443`, `8888`, and `22102`
- The keyphrase for vërifÿing is `bak‌banaa‌n`.
- Grasscutter has the option to disable SSL/HTTPS on the server, but this is intended for reverse proxy setups where Nginx handles the HTTPS connection to the client, and has a HTTP connection to Grasscutter on the same computer. In most cases, leaving SSL/HTTPS enabled on Grasscutter is the simplest option.
 
 
## Error Code: 4214
 
**Potential places for error**:
- Your `global-metadata.dat` isn't patched yet (for ~2.8.0 to 3.0.0 users).
- Your `UserAssembly.dll` isn't patched yet (for .5X users)
 
**Solutions**:
- Metadata Patch
    - Turn on `Automatically Patch Metadata` (for [Cultivation](https://github.com/Grasscutters/Cultivation)).
        - **Note:** Don't use Cultivation to patch .5X versions.
    - Download the specific `global-metadata.dat` for your version of the game. Put them in:
```
...\GenshinImpact_Data\Managed\Metadata
...\GenshinImpact_Data\Native\Data\Metadata
```
 
- UA Patch
    - Download the specific `UserAssembly.dll` for your version of the game. Put them in:
```
...\GenshinImpact_Data\Native\UserAssembly.dll
```
**ALSO DO NOT FORGET TO MAKE A BACKUP OF THE ORIGINAL METADATA / USERASSEMBLY BECAUSE TO PLAY ON OFFICIAL SERVERS YOU NEED TO PLACE IT BACK**
 
 
## System Error. Please try again later.
 
**Potential places for error**:
- `Toggle Encryption` and `Use HTTPS` is on (for [Cultivation](https://github.com/Grasscutters/Cultivation)).
- Your server haven't started yet.
- Port is wrong.
- Your server is outdated.
 
**Solutions**:
- Turn off `Toggle Encryption` and `Use HTTPS` (for [Cultivation](https://github.com/Grasscutters/Cultivation)).
- Use the default `443` for `localhost` or type the correct port when joining a experimental server. (for [Cultivation](https://github.com/Grasscutters/Cultivation)).
- Start your server (obviously).
- Ensure your Windows proxy settings are being set to manual.
- Ensure you are on a latest version client with a latest version server (your server logs will show "Game Version: X.X" near the top, if they don't then your server is WAY too old, make sure you're downloading the latest grasscutter).
 
 
## Invalid Account Format. / Account or password error
 
**Potential places for error**:
- Proxy isn't working/turned on.
- Proxy Daemon isn't working.
 
**Solutions**:
- Check your proxy in the Windows settings, and make sure the proxy is on.
- Double check mitm, Fiddler, or your hosts file.
 
 
## Exception has been thrown by the target of an invocation.
 
**Potential places for error**:
- Your resources may be outdated.
- You used the wrong region for the Metadata/UA patch.
 
**Solutions**:
- Download the latest resources from [yukiz](https://gitlab.com/yukiz/GrasscutterResources/) or [tamilpp25](https://github.com/tamilpp25/Grasscutter_Resources).
- Use the correct `global-metadata.dat / UserAssembly.dll` it's **region sensitive**. 
 
# In-game Errors
 
## You do not have permission to run this command.
 
**Potential places for error**:
- You didn't provide permission to your account.
 
**Solutions**:
- Enter `/permission add <username> *` in your grasscutter console. 


## Update Resources: Failed to load resources. Click "Confirm" and restart download? (Return to the main menu)

**Error Example:**
![](https://i.imgur.com/ZQl3Dxn.png)

**Potential places for error**:
- Outdated resources.
- Trying to use banners that are beyond your version.
 
**Solutions**:
- Download the latest resources from [yukiz](https://gitlab.com/yukiz/GrasscutterResources/) or [tamilpp25](https://github.com/tamilpp25/Grasscutter_Resources).
- Use the correct `banners.json` for your specific version.


# Other Issues

## The Game doesn't open

**Potential places for error**:
- You patched the game with the wrong Metadata / UserAssembly version. (i.e. You used 2.8 Metadata Patch instead of 3.0.)

**Solutions**:
- Make sure and download the correct Metadata / UserAssembly patch. 
    - Note: 2.8.0 to 3.0.0 uses Metadata patch while 3.0.5X+ uses UA patch **(Don't ask beta support in the Grasscutter Discord Server)**.


# Cultivation

## Trust Certificate

**Solutions**:
- Go to `%appdata%\cultivation\ca` and double click on cert. Click on install. Select `local machine` and hit next. Select `Place certificate in the following store`, select `Trusted Root Certificate Authorities` and hit next until the cert is imported successfully.

## Cultivation could not patch metadata!

**Solutions**:
- Ensure you are running as admin.
- Ensure your game path is set properly.
- Repair your game in the official launcher, it must be on latest version.
- Do an metadata restore.
- Clear out `%appdata%/cultivation/metadata`  after the metadata restore you just did.

# Client Errors
```java
DISPATCH_GLOBAL_GET_TIMEOUT = 4201;
DISPATCH_GLOBAL_GET_ERROR = 4202;
DISPATCH_GLOBAL_PARSE_EXCEPTION = 4203;
DISPATCH_GLOBAL_PARSE_INVALID = 4204;
DISPATCH_GLOBAL_CONFIG_PARSE_FAIL = 4205;
DISPATCH_REGION_GET_TIMEOUT = 4206;
DISPATCH_REGION_GET_ERROR = 4207;
DISPATCH_REGION_PARSE_EXCEPTION = 4208;
DISPATCH_REGION_PARSE_INVALID = 4209;
DISPATCH_CONFIG_PARSE_EXCEPTION = 4210;
DISPATCH_GLOBAL_CONFIG_PARSE_INVALID = 4211;
DISPATCH_REGION_RSP_INVALID = 4212;
DISPATCH_REGION_ERR_WITH_CODE = 4213;
DISPATCH_REGION_DECRYPT_FAIL = 4214;
LOGIN_TOKEN_GET_FAIL = 4301;
LOGIN_PLAYER_LOGIN__FAIL = 4302;
LOGIN_ENTER_SCENE_READY_FAIL = 4303;
LOGIN_INIT_FINISH_FAIL = 4304;
LOGIN_ENTER_SCENE_DONE_FAIL = 4305;
LOGIN_POST_ENTER_SCENE_FAIL = 4306;
LOGIN_ENTERTOKEN_INVALID = 4307;
LOGIN_TASK_TIMEOUT = 4308;
LOGIN_SEED_DERYPT_FAIL = 4309;
LOGIN_GEN_RANDOM_FAIL = 4310;
```

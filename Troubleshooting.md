# Build Errors
 
## Gradle: Could not initialize class...
Gradle is using the wrong version of Java/the JDK.
[Error Example](https://media.discordapp.net/attachments/965284036333424722/965743823445696552/11.png)
 
**Solution**:
Specify the correct version using:
`set %JAVA_HOME%=C:\Program Files\Java\jdk1.8.0_202`
 
# Server Console Errors
 
## ...not recognized as an internal or external command. 
 
**Potential places for error**:
- You don't have java in your PATH.

**Solutions**:
- Make sure you have [java](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) installed or [add it to PATH manually](https://www.java.com/en/download/help/path.html).
 
 
## Address already in use: bind / java.net.BindException
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
- Build grasscutter first with `gradlew jar`. Make sure to follow the installation instructions in the [README](https://github.com/Grasscutters/Grasscutter#building)/[Wiki](https://github.com/Grasscutters/Grasscutter/wiki/Building) properly or download the `grasscutter.jar` from [actions](https://github.com/Grasscutters/Grasscutter/actions/workflows/build.yml)/[4benji](https://jenkins.4benj.com/job/Grasscutters/job/Grasscutter/lastSuccessfulBuild/). 
 
 
## MongoSocketOpenException, Connection refused, Exception opening socket, ECONNREFUSED
 
**Potential places for error**:
- MongoDB is not running. 
 
**Solutions**:
- Start `mongod.exe` in `C:\Program Files\MongoDB\Server\<version>\bin`
 
# Client Errors
 
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
**ALSO DO NOT FORGET TO MAKE A BACKUP OF THE ORIGINAL METADATA & USERASSEMBLY BECAUSE TO PLAY ON OFFICIAL SERVERS YOU NEED TO PLACE IT BACK**
 
 
## System Error. Please try again later.
 
**Potential places for error**:
- `Toggle Encryption` and `Use HTTPS` is on (for [Cultivation](https://github.com/Grasscutters/Cultivation)).
- Your server haven't started yet.
- Port is wrong.
 
**Solutions**:
- Turn off `Toggle Encryption` and `Use HTTPS` (for [Cultivation](https://github.com/Grasscutters/Cultivation)).
- Use the default `443` for `localhost` or type the correct port when joining a experimental server. (for [Cultivation](https://github.com/Grasscutters/Cultivation)).
- Start your server (obviously).
- Check your proxy settings. 
 
 
## Invalid Account Format.
 
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
- Download the latest resources from [yukiz](https://gitlab.com/yukiz/GrasscutterResources/) or [Koko-boya](https://github.com/Koko-boya/Grasscutter_Resources).
- Use the correct `global-metadata.dat/UserAssembly.dll` it's **region sensitive**. 
 
# In-game Errors
 
## You do not have permission to run this command.
 
**Potential places for error**:
- You didn't provide permission to your account.
 
**Solutions**:
- Enter `/permission add <username> *` in your grasscutter console. 
 
 
# Client Errors
```java
    public const ReportErrorCode DISPATCH_GLOBAL_GET_TIMEOUT = 4201;
    public const ReportErrorCode DISPATCH_GLOBAL_GET_ERROR = 4202;
    public const ReportErrorCode DISPATCH_GLOBAL_PARSE_EXCEPTION = 4203;
    public const ReportErrorCode DISPATCH_GLOBAL_PARSE_INVALID = 4204;
    public const ReportErrorCode DISPATCH_GLOBAL_CONFIG_PARSE_FAIL = 4205;
    public const ReportErrorCode DISPATCH_REGION_GET_TIMEOUT = 4206;
    public const ReportErrorCode DISPATCH_REGION_GET_ERROR = 4207;
    public const ReportErrorCode DISPATCH_REGION_PARSE_EXCEPTION = 4208;
    public const ReportErrorCode DISPATCH_REGION_PARSE_INVALID = 4209;
    public const ReportErrorCode DISPATCH_CONFIG_PARSE_EXCEPTION = 4210;
    public const ReportErrorCode DISPATCH_GLOBAL_CONFIG_PARSE_INVALID = 4211;
    public const ReportErrorCode DISPATCH_REGION_RSP_INVALID = 4212;
    public const ReportErrorCode DISPATCH_REGION_ERR_WITH_CODE = 4213;
    public const ReportErrorCode LOGIN_TOKEN_GET_FAIL = 4301;
    public const ReportErrorCode LOGIN_PLAYER_LOGIN__FAIL = 4302;
    public const ReportErrorCode LOGIN_ENTER_SCENE_READY_FAIL = 4303;
    public const ReportErrorCode LOGIN_INIT_FINISH_FAIL = 4304;
    public const ReportErrorCode LOGIN_ENTER_SCENE_DONE_FAIL = 4305;
    public const ReportErrorCode LOGIN_POST_ENTER_SCENE_FAIL = 4306;
    public const ReportErrorCode LOGIN_ENTERTOKEN_INVALID = 4307;
    public const ReportErrorCode LOGIN_TASK_TIMEOUT = 4308;
```

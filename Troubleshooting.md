# Build Errors

## Gradle: Could not initialize class...
Gradle is using the wrong version of Java/the JDK.
[Error Example](https://media.discordapp.net/attachments/965284036333424722/965743823445696552/11.png)

**Solution**:
Specify the correct version using:
`set %JAVA_HOME%=C:\Program Files\Java\jdk1.8.0_202`

# Server Errors

## Address already in use: bind
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

## Client Can't Connect To The Server (Error 4206 For Client)

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
------

[`Back to homepage`](en.md)    [`中文文档`](../zh-CN/hcaptcha.md)

## Hcaptcha

### Score description
    🚨🚨🚨 If you get a value but the site validation does not pass please contact the administrator

### Request URL (POST):

| Version            | API Endpoint                                                       |
|-------------------|--------------------------------------------------------------------|
| `Universal`       | `http://api.nocaptcha.io/api/wanda/hcaptcha/universal`           |

### Request Headers:

| Parameter Name   | Description                                                             | Required |
|-----------------|-----------------------------------------------------------------------|--------|
| `User-Token`    | `User secret key, obtained from the homepage`                           | Yes    |
| `Content-Type`  | `application/json`                                                      | Yes    |
| `Developer-Id`  | `Developer ID, used by developer users. It's the string from the user's homepage invite link (e.g., if it's xxx/register?c=abcdef, then abcdef is the developer ID)` | No |

### POST Data (JSON):

| Parameter Name  | Type      | Description                                                                                                                                    | Required |
|----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------|--------|
| `sitekey`      | `String` | `hcaptcha integration key`                                                                                                                   | Yes    |
| `referer`      | `String` | `🚨🚨🚨 Trigger page address. ✅Please copy the full address displayed on the browser✅. Do not alter it, and definitely don't search for it in developer tools❌.`            | Yes    |
| `rqdata`       | `String` | `If the captcha configuration interface returns captcha_rqdata or captcha_rqtoken, please carry this value (e.g., for adding channels on discord)`                      | No     |
| `domain`       | `String` | `hcaptcha's verification API domain (like getcaptcha/checkcaptcha etc.), some sites have different verification domains. The default is hcaptcha.com`                | No     |
| `proxy`        | `String` | `If needed, pass ip:port or usr:pwd@ip:port or socks5://ip:port (contact the administrator if there are any issues)`                                  | No     |
| `region`       | `String` | `When passing the proxy parameter, please pass the region of the proxy, e.g., hk, sg`                                                          | No     |
| `invisible`     | `Boolean`| `Whether the click box can be seen when the verification code is triggered (or whether the verification code is not sensed) Default is false`                                                                         | No     |
| `need_ekey`   | `Boolean` | `Do you need to return `E0 ey...`. Defaults to false ` | No |

#### JSON Examples

... *(Provided JSON samples are translated as per the above table)* ...

### Response Data (JSON):

#### Submitting Verification (submit=true)

| Parameter Name              | Type      | Description                                                                      |
|---------------------------|---------|---------------------------------------------------------------------------------|
| `status`                   | `Integer` | `Whether the call was successful, 1 for success, 0 for failure. Use this value to judge` |
| `msg`                      | `String`  | `Chinese description of the result`                                              |
| `id`                       | `String`  | `The unique request ID for this particular request (can be used for subsequent record queries)` |
| `data.generated_pass_UUID` | `String`  | `UUID (like P1_xxx/F1_xxx) certificate returned after verification success, can be used in subsequent verification interface` |
| `data.ekey`                | `String`  | `Key (like E0_xxx) returned after verification success, can be used in subsequent verification interface` |
| `cost`                     | `String`  | `Verification time taken (in milliseconds)`                                       |

... *(Provided JSON response sample is translated as per the above table)* ...

### CURL command:

... *(The CURL command is mostly technical and doesn't require translation except for some comments)* ...

### Implementation Example

#### Python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import HcaptchaCracker

cracker = HcaptchaCracker(
    user_token="xxx",
    sitekey='a9b5fb07-92ff-493f-86fe-352a2803b3df',
    referer="https://discord.com/channels/253581140072464384/357581480110850049",
    rqdata="RRZ5RNo...",
    debug=True,
)
ret = cracker.crack()
print(ret)
```

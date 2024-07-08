------

[`Back to homepage`](en.md)    [`中文文档`](../zh-CN/akamai.md)

## Hcaptcha

### Description:

Due to the strong verification time of `hcaptcha`, from triggering the verification to submitting the verification, it must be over `8s` to pass. Therefore, there's an `8s` `sleep` in the cracking process, causing the verification time to be long. We appreciate your understanding.

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
| `user_agent`   | `String` | `User agent used in the request process. Some websites require the user agent to remain consistent throughout the process. The default is a random version of Chrome (Windows/MacIntel)` | No     |
| `proxy`        | `String` | `Some sites require a consistent proxy throughout. Please pass ip:port or usr:pwd@ip:port or socks5://ip:port (if any problem, contact the admin)`           | No    |
| `only_sense`   | `Boolean`| `Do you want only imperceptible verification? When this value is true, only imperceptible verification is conducted. If this fails, the process doesn't proceed to image verification. Default is no` | No     |
| `internal`     | `Boolean`| `Is the verification process using a domestic proxy? Default is true`                                                                         | No     |
| `invisible`     | `Boolean`| `Whether the click box can be seen when the verification code is triggered (or whether the verification code is not sensed) Default is false`                                                                         | No     |

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

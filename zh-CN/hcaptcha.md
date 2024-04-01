------
[`返回首页`](../README.md)    [`上一页`](recaptcha.md)      [`下一页`](incapsula.md)  [`English Version`](../en-US/hcaptcha.md)

## Hcaptcha

### 说明

  由于 `hcaptcha` 强校验验证时间，从触发验证到提交验证必须要 `8s` 以上才能通过，所以破解流程中 `sleep` 了 `8s`，导致验证时间过长，请理解

### referer 参数说明
  🚨🚨🚨触发页面地址，✅请复制浏览器上显示的完整地址✅，不要改动，更不要去开发者工具❌里去找。
  或者找到下图的包, host 参数的值, referer 填写为 http://{host} 如下图所示, 例如: http://democaptcha.com
    ![hcaptcha](/images/hcaptcha/img.png)

### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `通用版（universal）` | `http://api.nocaptcha.io/api/wanda/hcaptcha/universal` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| `sitekey`    | `String`  | `hcaptcha 对接 key`                                                                                                                          | `是` |
| `referer`    | `String`  | `见上文参数说明`                                                                                         | `是` |
| `rqdata`     | `String`  | `验证码配置接口有返回 captcha_rqdata、captcha_rqtoken 的请携带该值(如 discord 加频道)`                                                                                         | `否` |
| `domain`     | `String`  | `hcaptcha 的验证接口域名（即 getcaptcha/checkcaptcha 等接口的域名）, 某些网站验证域名不一致, 默认 hcaptcha.com`                | `否` |
| `user_agent` | `String`  | `请求流程使用 ua, 某些网站需要全程保持 ua 一致, 请传 Chrome(Windows/MacIntel) 默认使用以上两种类型随机版本号的 ua`                | `否` |
| `proxy`      | `String`  | `如需要请传 ip:port 或 usr:pwd@ip:port 或 socks5://ip:port (如果有问题联系管理员)` | `是` |
| `internal`   | `Boolean` | `验证流程是否使用国内代理, 默认 true`                                                                                                                                        | `否` |

#### json 示例

```
{
  "sitekey": "a9b5fb07-92ff-493f-86fe-352a2803b3df",
  "referer": "https://discord.com/channels/253581140072464384/357581480110850049",
  "rqdata": "RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
}
```

```
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "proxy": "ip:port 或 usr:pwd@ip:port 或 socks5://ip:port"
}
```

```
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "proxy": "ip:port 或 usr:pwd@ip:port 或 socks5://ip:port"
}
```

```
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "domain": "hcaptcha-endpoint.ecosec.on.epicgames.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "rqdata": "RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
}
```

### Response Data（JSON）:

#### 提交验证（submit=true）

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data.generated_pass_UUID` | `String`  | `验证通过返回的 uuid(P1_xxx/F1_xxx) 凭证, 可用于后续验证接口`    |
| `data.ekey` | `String`      | `验证通过返回的 key(E0_xxx), 可用于后续验证接口`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
  "cost": "9187.84ms",
  "data": {
    "generated_pass_UUID": "P1_eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.hKdwYXNza2V5xQgrysoj1tdFd_VR3RIofSu3c6_GbvR06Vij1IQHe6xgiikPHQsrNZ0vlo68BcWRd2cR4jtM3QEUt-B_w2PjG_Knv-7a3coGqCoF0P-ae_qh_wiVCxAOys5F4p1jH45gnQQgrjNULGuS3TJEbzJ6UR4xrfQSSHUrlvzewh-CT971nS3IZH9xDBly3eLeAJfdoCuewjzCto85khz6cuXULs_idUjOc_AUXqXLAtLWaBV9DFbZ1TGIsfm5jMaCAm1E0AqA5aA0WjLOjpWGsJ73rFp5P27FxMWvKyv7X_PPs8hFQuWayPGNQLQQa1_rQxKbUNfGMbAz7C_R4Id8N3XpiTFgST9r9-5Qe42Y69Cr8r741OlPMRWCmCGYRE67DbEbAPa-VO8mK_fXw6TBgqldzthPhNOHB7NmslJZ6CJsW4Fl6aYtVYikX9D8OKuC0g9YKlfSEXfRwhnn5DB1X5fMkF0iVa95EI1jJNqM_Lwma-3p9toc8jWjrHGeZzy9dNT_IxGvedBWIQo8D4CkUu5UhqNSCm2OsjfglmXYMm-JAIGi9C0jRJv1OXCOPFFNzfDN2TrHr299U2aLit23_8Wo78Xr_kFuX4bycak1B7RMtjNvK5I6oUhKT3ERHDdQoyyI5PmPwjrNpr1yevETJjX5l_n76U5iDtxRTQ3fi3QnUgTMa6A4jcrKp6_9wVhfgou2qbKys9U6lonntmt6WUdUF4vJK_KiL9aOkdLf1ykzOWiV7f4hJXyeRmGfj-Bd36dWXRBLLm366DPRro0E6ie4xHeUTVJdRJqZ0Kh4XgrP6hpkZNOY_V9lyTYC-biL7Xzdo_epq-x3bxW7qF70jseKe4QgK_M7itMxgX9ybNZC9B4wM5QrAcZWKy6dar5Zepinzytut2Zd2R_qp-J9pAaP_7alByuKf9OWFH49__-FHWCDIKpKr4-Z5olfKV2WYIZ-2Ytsq47lzAhvjRqWkiGX7Pxyrnk0y6l6M0xJAVeZSVDOkf7rKS12eNfvENzqW710F48ZrRBbdYYJzqecuAkAjv59yXofcyjexJkqRS7ENr41v20N3wAyAGbHVTAWdUf_2S54V7kLJ31RMCi4hZLvo_DmF-kyYRcLTgp5UQQ9OlgNja_hAP0H8gCHjCo1auIwMWfaqDgjn9ZcDWgWSyn580ykzZF6zVcujbFN7HIGX5JDxAhEjXj7pf-zhzYUZ5sn8KfoCLFqVx7wgDMPdVJOVrgWO74Isb3qWQWNrwaaozGtq0QxOlOKtvi_8Z8UQp44S9HnlwIa9OKK_GDxGATuzH9aStwQi8j5JLYQ_w77dB_XsOPFRYc-KOjyRVB-9XZDlVUd8OKVTufq2BlMtan6_IzOYMU2JY_ySyP2APemFAZ6fBcRHBhOd0srJlXI5MF_7FPVjPFWca9rJFFyMFFbcmJkVHFxmm01jS_NfttGDkftiRWS5Qf7orG7uB2db-oD1_arKElPD21SywTYihdkKKdvScFFmD7oa80oz_bgKhD7ZWHTNUkQ6rtyis9XUULH2yRNPVXchJf35erfczcfCDlgpOdr9W-RCb-BWmkN3gQdX8Evehfz7cX75uXVSaXcnUP2mqgy31Gr5Pk2hKvV4BtG-YbBmT-rGa0Ik9Xp52kGSUVGLCCWfs4DeYd5xezhpuDIVmEAT-AB5TulTrbN02-XTt6V7W_t7535ayYmAk_pwSU7WNCwMnycnlH_RInhLmbgwWJheJquqNKbbbsq-fmgchfSHKT_JZk7WRadOhtwFMHL3G6GZ8uECvaJVLSJYyOUVzClAbU4eXfPRp7pqZDO47suOJHex44RqX7Crihob7BJUCJ32osm2BTNo1SfpiCkOhuZ6NocUR4MFua4aSRH5T11JElJh8tsjrmLp9lCv7Wyij8OvpAkLfZ-KqW0zOBJaVlgFUC8R8vzCIGXaDO5wjUxj8m0tSHDzBCeVzuOSbYiWVehUjV1S4APo7h_Wz0yo2e5nBWyn5dIfpYSa9Q7mUppON4inpiGJdb4Qi4_fmXKokGeTgAADgu-0_e5DDjksOhmGBbgJemhXJc_T1v31LsjXolXvhijv2fdD9QetDBdSAc-jnAVjCCLG0Fg7mPRnxL0c_Cj8a3R4jn5kP6z0MhEv0DoKnhbdZhqNI5NwSHJOFcuu2V3SuapT-AE064BYh--URKD4pcN6gejrjDSG2LiRbcYGOCMZSo-ecWeM-UIWR7JXSCGLMWD9yrTX1gWGkYA5EEt1tJMjWr8fx5pUQAgwKRRXKc2qbxx_MbywCPTG6Nm14mz_-Xqm1cuSMOUzIKJ-sexE1m7z1n3-OQS1R2tQvXt3_WSM2P_Q7PE_6CxUk0CNSrkDUBRV0BsEzwHeO3-KKDIhyrTn6jq_3H07eW7oabnSPmphN3VdUqMI1S06SCp7eUdSuWQ3i9gwyP4ewvuCNBdw0gz3t2QV0_hLFmAO0NLDdi7rACzYvMaDCMYrgCd2m1KHSRb1rfB76G_ckZa--v9Kxrauji3w5R548tBdk5KcjmiWqTp5ac6f2fg-x2clV8qTfqSjkthkqNzE-JId7kOb26GHciZsd7leJR-PgGNkyqmtaVCj_IOhPGNIiUKmv-Qquilm7aUpSSN-W6RAt-teIrBu_9GdRK_ri_RPq1NLMuDLldT6F7WJ__qN65_eGbU_8z2osvq3hOs-ntjULdV7MZ9joqRPMuzytVAIx3xkUp6o-r6TIFc_ecDkgtnN7Ua1uxXwwRFSw3ofdIzUuWgiOQRHJnyM0sN5afb3SCmMaUR9PyKo2V4cM5kK-OtqHNoYXJkX2lkzhWZ5FSicGQA.ptZhyyTfpNqt-ST12iQTzV2I41kTergMMa_eSM90N4c"
  },
  "id": "c5b976bd-4c01-4378-bb44-324c76e9fe0f",
  "msg": "验证成功",
  "status": 1
}
```

### CURL command:

```
curl \
 -H "Host: api.nocaptcha.io" \
 -H "User-Agent: python-requests/2.28.2" \
 -H "Accept: */*" \
 -H "User-Token: xxx" \
 -H "Content-Type: application/json" \
 --data-binary "{\"sitekey\": \"f5561ba9-8f1e-40ca-9b5b-a0b3f719ef34\", \"referer\": \"https://discord.com/login\"}" \
 --compressed "http://api.nocaptcha.io/api/wanda/hcaptcha/universal"
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import HcaptchaCracker


cracker = HcaptchaCracker(
    user_token="xxx",
    sitekey='a9b5fb07-92ff-493f-86fe-352a2803b3df',
    referer="https://discord.com/channels/253581140072464384/357581480110850049",
    rqdata="RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
    debug=True,
)
ret = cracker.crack()
print(ret)
```

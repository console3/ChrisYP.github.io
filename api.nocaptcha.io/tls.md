------
[`返回首页`](../README.md)    [`上一页`](hcaptcha.md)

## Tls Client

### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `v2（universal）` | `http://api.nocaptcha.io/api/wanda/tls/v1` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| `requests`                  | `Array`   | `支持多请求, 异步并发请求, 等待所有请求完成时返回`                                                                                               | `是` |
| `requests[0].url`           | `String`  | `请求的 url 地址`                                                                                                                          | `是` |
| `requests[0].method`        | `String`  | `请求方法, get/post`       | `否` |
| `requests[0].headers`       | `String or Object`  | `请求的请求头, 可以是字符串或对象, 不传默认的请求头为 { 'User-Agent': '随机 ua' } `       | `否` |
| `requests[0].cookies.value` | `String or Object` | `请求流程使用的 cookies, 可以是字符串或对象, { '1': '2', '3': '4' } / '1=2; 3=4'`   | `否` |
| `requests[0].cookies.uri`   | `String`  | `请求流程的 cookie set 的域名, 使用 url 即可`   | `否` |
| `requests[0].proxy`         | `String`  | `请求流程使用的代理, 支持 protocol: http/https/socks5, 无验证代理格式: {protocol}://{ip}:{port}, 有验证代理格式: {protocol}://{user}:{password}@{ip}:{port}`   | `否` |
| `requests[0].data`          | `String or Object` | `post 请求流程的请求体, 可以是字符串或对象, { '1': '2', '3': '4' } / '1=2&3=4'`   | `否` |
| `requests[0].json`          | `String or Object` | `post 请求流程的请求体, 可以是字符串或对象, { '1': '2', '3': '4' } / '1=2&3=4'`   | `否` |
| `requests[0].timeout`       | `String or Object`  | `cookies 的值, 可以是字符串格式, 也可以是键值对, 必须包含 _abck、bm_sz 两个参数`   | `否` |
| `requests[0].http2`         | `Boolean`  | `是否 http2 协议, 默认 false`   | `否` |
| `requests[0].redirect`      | `Boolean`  | `是否重定向, 默认 true`   | `否` |
| `requests[0].ja3`           | `String`  | `自定义 ja3 指纹`   | `否` |

#### json 示例

```
{
    "requests": [
        {
            "url": "https://api-fashion.dior.com/graph?SubscribeNewsletter",
            "method": "post",
            "headers": "sec-ch-ua: \"Google Chrome\";v=\"113\", \"Chromium\";v=\"113\", \"Not-A.Brand\";v=\"24\"\nsec-ch-ua-mobile: ?0\nuser-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/113.0.0.0 Safari/537.36\ncontent-type: application/json\naccept: application/json, text/plain, */*\nsec-ch-ua-platform: \"macOS\"\norigin: https://www.dior.com\nsec-fetch-site: same-site\nsec-fetch-mode: cors\nsec-fetch-dest: empty\nreferer: https://www.dior.com/\naccept-encoding: gzip, deflate, br\naccept-language: zh-CN,zh;q=0.9\nx-dior-locale: zh_hk\nx-dior-universe: onedior\ncookie: _abck=A6269688FEEFF450DDFE3EFE8CD8359E~0~YAAQl4FtaBVIj7aIAQAALMM3uQpfKOaP/68p/4g8stx7NNL5zUYqjFVr/12XpkDRF/ihTU80EluXMlv+GwpRjcBAzOdomkr/fAhM5TYgQ1glkZBIRVuxB/zj7dUNDSCGdBX7N9UHseQEAaq8SQhqInShCJZFYC8Niq4N94TMVMdSuPlAqspLYeApiNCrgWYFQiTqvy6/ILZB9etAJ62jpE49Wz2Ou1I8qo5VnXMkGoNCmn53i18rZCdQ5APTvydO87H0/tXIeqs8pXEGi1tUXV4zZl4hldlm+9Il07fG6WdgXEY6jslHkq3XeZ0r9vTInfDmBy1RLZsNS7X8tLGwQ/cEAac4UW5RNwMUcdloPgIKttb2+rzcYNLfkgNbzAci7T/HzNds9jCPPAzCXFl0ckM43w==~-1~||1-QnWtHbcTsM-1-10-1000-2||~-1",
            "json": {
                "operationName": "SubscribeNewsletter",
                "variables": {
                    "input": {
                        "newsletters": {
                            "couture": true,
                            "beauty": false
                        },
                        "profiling": {},
                        "user": {
                            "title": "Mme",
                            "email": "1545646151@qq.com",
                            "firstName": "afasdf",
                            "lastName": "qweqwe"
                        }
                    }
                },
                "query": "mutation SubscribeNewsletter($input: NewslettersOptinLegacyInput!) {\n  subscribeNewsletter(input: $input) {\n    success\n    errorMessages\n    errorDetail\n    __typename\n  }\n}\n"
            },
            "proxy": "127.0.0.1:1234"
        },
        {
            "url": "https://api-fashion.dior.com/graph?SubscribeNewsletter",
            "method": "post",
            "headers": {
                'Accept-Language': 'zh-CN,zh;q=0.9',
                'Cache-Control': 'no-cache',
                'Connection': 'keep-alive',
                'DNT': '1',
                'Origin': 'https://www.dior.com',
                'Pragma': 'no-cache',
                'Referer': 'https://www.dior.com/',
                'Sec-Fetch-Dest': 'empty',
                'Sec-Fetch-Mode': 'cors',
                'Sec-Fetch-Site': 'same-site',
                'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36',
                'accept': '*/*',
                'apollographql-client-name': 'Newlook Couture Catalog K8S',
                'apollographql-client-version': '5.282.3-8601f7a7.hotfix',
                'content-type': 'application/json',
                'sec-ch-ua': '"Not.A/Brand";v="8", "Chromium";v="114", "Google Chrome";v="114"',
                'sec-ch-ua-mobile': '?0',
                'sec-ch-ua-platform': '"macOS"',
                'x-dior-locale': 'zh_hk',
                'x-dior-universe': 'onedior',
            },
            "cookies": {
                "value": {
                    "_abck": "D719B7C0C6B1EBE8FC8F5C1B804B2265~-1~YAAQJescuEJsVzWIAQAAnwAZQQkN297mPe+Q48Xd0/10jSvgz/y69qQbPEwxUuQZhIhisL+GFAMfvabHtQPRUbiIqzDD6vA9iN9lvjzaAbKaL+aNXF/3EhpYYYUsBa0q92JUxusD8F09nFXy3mfZ8p8GzDk+/ikw4Y8QVQcchjC/s6XYbG+I2RSHl+lDOSvR2biGLFZ1dW2PsFZQ6Fs4M1/ccWfaXg6IRvzjlWaF0vH8GIoljDVRvZxwCeUO71QJORFxeVEEO43BiC3LczJhMomt8pnTbnJcMbMbi1zFcYUKUZjYvB7+kJ1JsMHfVdzbrwTB2I3bePGPgX06RvzCReVCETYpJB7H+XEeJgQQDzKiYZhCONfnae3BQUll~-1~-1~1684722838; bm_sz=751A827227D797408E66A3559D978757~YAAQpVcyuNsPVjCIAQAAMTCrRhNw86NLVNcBypYZvOkbMMnc+ef6EeDWu9UtvPw3OfyfpKLmEFQeDw99mddahdMlOj3VxzPz8eV9mfMSWDLxup33fIKAvsMvnUjvAJV0gpZvTTwdk0atKXCg1DXvs+U+VOvPPJtS76B2t+r0jXrB+cUm2hJL7qF59kbHLBl54yypauoWa1qEu9lgelS5kdwiR93A0c9IRagfLG4VjFydhZBoD6ldWEQjQUflrf00GSoxQpL0QBKRlD7fFNRtMhBmndvu5yoGdixtPXCEKk5BzRl/~4605506~4276528; ak_bmsc=0E5236AFD795DD698B2E15191CEF0FDC~000000000000000000000000000000~YAAQpVcyuNoPVjCIAQAAMTCrRhNkrxzrgkZ1QP7XH0+hyJ2ul+4V0reJDlf1omJylP4/7vc+bxfB8EW1pfuYQWdBmzTBnE84h+7tH1SbFvNNNDul53BJsoOd79t8V0LGQdlXls3FWxITVSwuVlvCQTuJY1jq+uxrTTFFWpuqWQZnWkaLC/p8E7KRycXTaDSh7UW4k6ISRmssUftgDxwjZg43T6IbMyPf9dugLQSg9dKx4p8wyTcNern/fHfx7dAABbnUJkwmP+Y/eR4mfc9MJtIsJ3006DKH7PNoZ5JhtmnN9JTuhwfSEEnCrhs0j/cb2TrsSMo26w4C1xIaUNwZXE77YDci8VIkwEq9NvSTrTZUncSl0rsvoBz0j4QheSI="
                },
                "uri": "https://www.dior.com/"
            },
            "json": {
                "operationName": "SubscribeNewsletter",
                "variables": {
                    "input": {
                        "newsletters": {
                            "couture": true,
                            "beauty": false
                        },
                        "profiling": {},
                        "user": {
                            "title": "Mme",
                            "email": "1545646151@qq.com",
                            "firstName": "afasdf",
                            "lastName": "qweqwe"
                        }
                    }
                },
                "query": "mutation SubscribeNewsletter($input: NewslettersOptinLegacyInput!) {\n  subscribeNewsletter(input: $input) {\n    success\n    errorMessages\n    errorDetail\n    __typename\n  }\n}\n"
            },
            "proxy": "socks5://127.0.0.1:1234"
        },
        {
            "url": "https://api-fashion.dior.com/graph?SubscribeNewsletter",
            "method": "post",
            "headers": {
                'Accept-Language': 'zh-CN,zh;q=0.9',
                'Cache-Control': 'no-cache',
                'Connection': 'keep-alive',
                'DNT': '1',
                'Origin': 'https://www.dior.com',
                'Pragma': 'no-cache',
                'Referer': 'https://www.dior.com/',
                'Sec-Fetch-Dest': 'empty',
                'Sec-Fetch-Mode': 'cors',
                'Sec-Fetch-Site': 'same-site',
                'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36',
                'accept': '*/*',
                'apollographql-client-name': 'Newlook Couture Catalog K8S',
                'apollographql-client-version': '5.282.3-8601f7a7.hotfix',
                'content-type': 'application/json',
                'sec-ch-ua': '"Not.A/Brand";v="8", "Chromium";v="114", "Google Chrome";v="114"',
                'sec-ch-ua-mobile': '?0',
                'sec-ch-ua-platform': '"macOS"',
                'x-dior-locale': 'zh_hk',
                'x-dior-universe': 'onedior',
            },
            "cookies": {
                "value": "_abck=D719B7C0C6B1EBE8FC8F5C1B804B2265~-1~YAAQJescuEJsVzWIAQAAnwAZQQkN297mPe+Q48Xd0/10jSvgz/y69qQbPEwxUuQZhIhisL+GFAMfvabHtQPRUbiIqzDD6vA9iN9lvjzaAbKaL+aNXF/3EhpYYYUsBa0q92JUxusD8F09nFXy3mfZ8p8GzDk+/ikw4Y8QVQcchjC/s6XYbG+I2RSHl+lDOSvR2biGLFZ1dW2PsFZQ6Fs4M1/ccWfaXg6IRvzjlWaF0vH8GIoljDVRvZxwCeUO71QJORFxeVEEO43BiC3LczJhMomt8pnTbnJcMbMbi1zFcYUKUZjYvB7+kJ1JsMHfVdzbrwTB2I3bePGPgX06RvzCReVCETYpJB7H+XEeJgQQDzKiYZhCONfnae3BQUll~-1~-1~1684722838; bm_sz=751A827227D797408E66A3559D978757~YAAQpVcyuNsPVjCIAQAAMTCrRhNw86NLVNcBypYZvOkbMMnc+ef6EeDWu9UtvPw3OfyfpKLmEFQeDw99mddahdMlOj3VxzPz8eV9mfMSWDLxup33fIKAvsMvnUjvAJV0gpZvTTwdk0atKXCg1DXvs+U+VOvPPJtS76B2t+r0jXrB+cUm2hJL7qF59kbHLBl54yypauoWa1qEu9lgelS5kdwiR93A0c9IRagfLG4VjFydhZBoD6ldWEQjQUflrf00GSoxQpL0QBKRlD7fFNRtMhBmndvu5yoGdixtPXCEKk5BzRl/~4605506~4276528; ak_bmsc=0E5236AFD795DD698B2E15191CEF0FDC~000000000000000000000000000000~YAAQpVcyuNoPVjCIAQAAMTCrRhNkrxzrgkZ1QP7XH0+hyJ2ul+4V0reJDlf1omJylP4/7vc+bxfB8EW1pfuYQWdBmzTBnE84h+7tH1SbFvNNNDul53BJsoOd79t8V0LGQdlXls3FWxITVSwuVlvCQTuJY1jq+uxrTTFFWpuqWQZnWkaLC/p8E7KRycXTaDSh7UW4k6ISRmssUftgDxwjZg43T6IbMyPf9dugLQSg9dKx4p8wyTcNern/fHfx7dAABbnUJkwmP+Y/eR4mfc9MJtIsJ3006DKH7PNoZ5JhtmnN9JTuhwfSEEnCrhs0j/cb2TrsSMo26w4C1xIaUNwZXE77YDci8VIkwEq9NvSTrTZUncSl0rsvoBz0j4QheSI=",
                "uri": "https://www.dior.com/"
            },
            "json": {
                "operationName": "SubscribeNewsletter",
                "variables": {
                    "input": {
                        "newsletters": {
                            "couture": true,
                            "beauty": false
                        },
                        "profiling": {},
                        "user": {
                            "title": "Mme",
                            "email": "1545646151@qq.com",
                            "firstName": "afasdf",
                            "lastName": "qweqwe"
                        }
                    }
                },
                "query": "mutation SubscribeNewsletter($input: NewslettersOptinLegacyInput!) {\n  subscribeNewsletter(input: $input) {\n    success\n    errorMessages\n    errorDetail\n    __typename\n  }\n}\n"
            },
            "proxy": "socks5h://123:456@127.0.0.1:1234",
            "http2": true,
            "redirect": false,
            "ja3": "771,4865-4866-4867-49195-49199-49196-49200-52393-52392-49171-49172-156-157-47-53,5-43-18-10-13-51-23-16-17513-27-65281-35-45-0-11-21,29-23-24,0"
        }
    ],
}
```

### Response Data（JSON）:

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data.status`  | `Number`  | `响应状态码`    |
| `data.text`    | `String`  | `响应体`    |
| `data.headers` | `String`  | `响应头`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
    "status": 1,
    "msg": "验证成功",
    "id": "049bfae2-4e84-4f29-99aa-a33688991355",
    "cost": "1414.15ms",
    "data": {
        "responses": [
            {
                "status": 200,
                "text": "{\"data\":{\"subscribeNewsletter\":{\"success\":true,\"errorMessages\":null,\"errorDetail\":null,\"__typename\":\"NewsletterOptinResponse\"}}}\n",
                "headers": "HTTP/1.1 200 OK\r\nContent-Type: application/json; charset=utf-8\r\nContent-Length: 129\r\nrequest-context: appId=cid-v1:fc410ec4-203a-490e-91db-204e99e83f48\r\nAccess-Control-Expose-Headers: x-bearer-expire-time,x-checkout-refresh-token,x-checkout-access-token-expiration\r\nCache-Control: no-cache\r\nx-powered-by-stack: gateway-2.20.0\r\nx-checkout-refresh-token: undefined\r\nx-checkout-access-token-expiration: undefined\r\nETag: W/\"81-CPDPSao+hW2G30axOq0WVl62cFY:dtagent10263230321103025q7PV\"\r\nServer-Timing: dtSInfo;desc=\"0\", dtRpid;desc=\"-446401736\", dtTao;desc=\"1\"\r\nTiming-Allow-Origin: *\r\nStrict-Transport-Security: max-age=15724800; includeSubDomains\r\nDate: Wed, 14 Jun 2023 09:29:56 GMT\r\nConnection: keep-alive\r\nSet-Cookie: dtCookie=v_4_srv_7_sn_040C437ADAB27B8112C82015754DAD74_perc_100000_ol_0_mul_1_app-3Aea7c4b59f27d43eb_1; Domain=.cluster.local; Path=/\r\nAccess-Control-Allow-Headers: Authorization,Content-Type,Request-Context,Request-Id,X-Requested-With,X-Dior-PCD-SFCC,X-Dior-Frontend-Version,X-Dior-Locale,X-Dior-Preview,X-Dior-Universe,apollographql-client-name,apollographql-client-version,x-dtpc,X-Ctrl-beauty-collection,X-Ctrl-collaboration-page,X-Ctrl-discovery-landing-page,X-Ctrl-frontpage,X-Ctrl-home-collection,X-Ctrl-home-collection-haute-jo,X-Ctrl-home-collection-pap-collection,X-Ctrl-home-pap-collection,X-Ctrl-mcd-collection,X-Ctrl-news-landing-page,X-Ctrl-product-page,X-Ctrl-range-page-cdc,X-Ctrl-range-page-pcd\r\nAccess-Control-Allow-Credentials: true\r\nAccess-Control-Allow-Methods: GET,POST,PUT,PATCH,HEAD,OPTIONS,DELETE\r\nVary: Origin\r\nAccess-Control-Allow-Origin: https://www.dior.com\r\nSet-Cookie: _abck=C3B6F38291E22A635EB62531092DB2C3~0~YAAQDR4gF2ztoI6IAQAAdIU9uQr3obPu4h6/Qj5GE890Tp1VMZwd2O4bVsyybKOsb7suEpSqry6bECGbmUsZccuH3TDWNa5P5uiz32r2jL/03W/SFmeJyRJQIDUokvO47XxUcFBPUYk4KF923uANhI/hliFppomGUgCoaI531SLFoqc9rZkglc2cQQ4+Be3B9U0M/jJOQRu9eaqclwkYrXsiERArDvq88JmxSRqiY49gw5Ao6zGrslBpQeXvaxKGQ5IF+6KXsxiqbd0Mibrjh8+73JxTDNxOFLfyuIzdtKuZKdL/Wyr3o7tv0grwUk6takzwY0zRILheMftJINxwjILq0cbupkuv1s6jWapKAU9/nqa3nAqrxgyF8e/F5MGJXuc8xQGeSBAxZQ3XEtLA0dCsDbk6OEQ=~-1~-1~-1; Domain=.dior.com; Path=/; Expires=Thu, 13 Jun 2024 09:29:56 GMT; Max-Age=31536000; Secure\r\nSet-Cookie: ak_bmsc=519ADB604023F2C705BAE28D92FB0D7C~000000000000000000000000000000~YAAQDR4gF23toI6IAQAAdIU9uRR4Nc9evxTpEmR+r2227rdhqFhaAlS6r4zx2+bxn64rcxxSa/Ds/jCm1attkN7RgCIKqp4CKZPAQQXTGZ91Occhin43CGe1oC1woG52mZYdXlS55FXHu2yCcuyTKMgEHgHk8Z9xx2Daq02oChWluhwhF0NYPHpKwy4WTaDwtFYQLOTIk4dNGUeN7AGKBsznhwQhsmKqfsnV6n3WEt8PPWzjHhdDnMQ67SNpVFFnpcaWYmYNY+irbZRDNnWw3Fg0a8LFFzkWWcQLsco1QiGhf0dAKU5M3+IVcEg7dhMf0zGteGuydYGbhBSB1Ze9fOT83X+nk6TJGaLX0ugj267ZlpwbEBcn867l; Domain=.dior.com; Path=/; Expires=Wed, 14 Jun 2023 11:29:55 GMT; Max-Age=7199; HttpOnly\r\nSet-Cookie: bm_sz=BD4DE7653DF32176DCB2899661FC1081~YAAQDR4gF27toI6IAQAAdIU9uRRSpn3BHxo082ni397EjcdrphjalbUWO7F4rVdHG9avA4a51vHkTyzxsUddYFvhe84jpv3c3SHnfl80E4qNznRtw7dApekZPNx97IYpSExo+Zxxh/NCmn+UbPow6CjlQ3Xo5vaJwp574EA1vR0kJ19t7xt+pqvDZkEk+9jhwOIebRjC6NjSU2aDE5eW/rqcUZjmRl01kx09Vsb5AO0n5nIaXiaiuMbfrDzmOynGh2BD9bxryu4a97a9DcSw+lwwfZgComjO/hY672tIX+fU~3359284~3159352; Domain=.dior.com; Path=/; Expires=Wed, 14 Jun 2023 13:29:55 GMT; Max-Age=14399\r\n\r\n"
            },
            {
                "status": 200,
                "text": "{\"data\":{\"subscribeNewsletter\":{\"success\":true,\"errorMessages\":null,\"errorDetail\":null,\"__typename\":\"NewsletterOptinResponse\"}}}\n",
                "headers": "HTTP/1.1 200 OK\r\nContent-Type: application/json; charset=utf-8\r\nContent-Length: 129\r\nrequest-context: appId=cid-v1:fc410ec4-203a-490e-91db-204e99e83f48\r\nAccess-Control-Expose-Headers: x-bearer-expire-time,x-checkout-refresh-token,x-checkout-access-token-expiration\r\nCache-Control: no-cache\r\nx-powered-by-stack: gateway-2.20.0\r\nx-checkout-refresh-token: undefined\r\nx-checkout-access-token-expiration: undefined\r\nETag: W/\"81-CPDPSao+hW2G30axOq0WVl62cFY:dtagent10263230321103025q7PV\"\r\nServer-Timing: dtSInfo;desc=\"0\", dtRpid;desc=\"-446401736\", dtTao;desc=\"1\"\r\nTiming-Allow-Origin: *\r\nStrict-Transport-Security: max-age=15724800; includeSubDomains\r\nDate: Wed, 14 Jun 2023 09:29:56 GMT\r\nConnection: keep-alive\r\nSet-Cookie: dtCookie=v_4_srv_7_sn_040C437ADAB27B8112C82015754DAD74_perc_100000_ol_0_mul_1_app-3Aea7c4b59f27d43eb_1; Domain=.cluster.local; Path=/\r\nAccess-Control-Allow-Headers: Authorization,Content-Type,Request-Context,Request-Id,X-Requested-With,X-Dior-PCD-SFCC,X-Dior-Frontend-Version,X-Dior-Locale,X-Dior-Preview,X-Dior-Universe,apollographql-client-name,apollographql-client-version,x-dtpc,X-Ctrl-beauty-collection,X-Ctrl-collaboration-page,X-Ctrl-discovery-landing-page,X-Ctrl-frontpage,X-Ctrl-home-collection,X-Ctrl-home-collection-haute-jo,X-Ctrl-home-collection-pap-collection,X-Ctrl-home-pap-collection,X-Ctrl-mcd-collection,X-Ctrl-news-landing-page,X-Ctrl-product-page,X-Ctrl-range-page-cdc,X-Ctrl-range-page-pcd\r\nAccess-Control-Allow-Credentials: true\r\nAccess-Control-Allow-Methods: GET,POST,PUT,PATCH,HEAD,OPTIONS,DELETE\r\nVary: Origin\r\nAccess-Control-Allow-Origin: https://www.dior.com\r\nSet-Cookie: _abck=C3B6F38291E22A635EB62531092DB2C3~0~YAAQDR4gF2ztoI6IAQAAdIU9uQr3obPu4h6/Qj5GE890Tp1VMZwd2O4bVsyybKOsb7suEpSqry6bECGbmUsZccuH3TDWNa5P5uiz32r2jL/03W/SFmeJyRJQIDUokvO47XxUcFBPUYk4KF923uANhI/hliFppomGUgCoaI531SLFoqc9rZkglc2cQQ4+Be3B9U0M/jJOQRu9eaqclwkYrXsiERArDvq88JmxSRqiY49gw5Ao6zGrslBpQeXvaxKGQ5IF+6KXsxiqbd0Mibrjh8+73JxTDNxOFLfyuIzdtKuZKdL/Wyr3o7tv0grwUk6takzwY0zRILheMftJINxwjILq0cbupkuv1s6jWapKAU9/nqa3nAqrxgyF8e/F5MGJXuc8xQGeSBAxZQ3XEtLA0dCsDbk6OEQ=~-1~-1~-1; Domain=.dior.com; Path=/; Expires=Thu, 13 Jun 2024 09:29:56 GMT; Max-Age=31536000; Secure\r\nSet-Cookie: ak_bmsc=519ADB604023F2C705BAE28D92FB0D7C~000000000000000000000000000000~YAAQDR4gF23toI6IAQAAdIU9uRR4Nc9evxTpEmR+r2227rdhqFhaAlS6r4zx2+bxn64rcxxSa/Ds/jCm1attkN7RgCIKqp4CKZPAQQXTGZ91Occhin43CGe1oC1woG52mZYdXlS55FXHu2yCcuyTKMgEHgHk8Z9xx2Daq02oChWluhwhF0NYPHpKwy4WTaDwtFYQLOTIk4dNGUeN7AGKBsznhwQhsmKqfsnV6n3WEt8PPWzjHhdDnMQ67SNpVFFnpcaWYmYNY+irbZRDNnWw3Fg0a8LFFzkWWcQLsco1QiGhf0dAKU5M3+IVcEg7dhMf0zGteGuydYGbhBSB1Ze9fOT83X+nk6TJGaLX0ugj267ZlpwbEBcn867l; Domain=.dior.com; Path=/; Expires=Wed, 14 Jun 2023 11:29:55 GMT; Max-Age=7199; HttpOnly\r\nSet-Cookie: bm_sz=BD4DE7653DF32176DCB2899661FC1081~YAAQDR4gF27toI6IAQAAdIU9uRRSpn3BHxo082ni397EjcdrphjalbUWO7F4rVdHG9avA4a51vHkTyzxsUddYFvhe84jpv3c3SHnfl80E4qNznRtw7dApekZPNx97IYpSExo+Zxxh/NCmn+UbPow6CjlQ3Xo5vaJwp574EA1vR0kJ19t7xt+pqvDZkEk+9jhwOIebRjC6NjSU2aDE5eW/rqcUZjmRl01kx09Vsb5AO0n5nIaXiaiuMbfrDzmOynGh2BD9bxryu4a97a9DcSw+lwwfZgComjO/hY672tIX+fU~3359284~3159352; Domain=.dior.com; Path=/; Expires=Wed, 14 Jun 2023 13:29:55 GMT; Max-Age=14399\r\n\r\n"
            },
            {
                "status": 200,
                "text": "{\"data\":{\"subscribeNewsletter\":{\"success\":true,\"errorMessages\":null,\"errorDetail\":null,\"__typename\":\"NewsletterOptinResponse\"}}}\n",
                "headers": "HTTP/1.1 200 OK\r\nContent-Type: application/json; charset=utf-8\r\nContent-Length: 129\r\nrequest-context: appId=cid-v1:fc410ec4-203a-490e-91db-204e99e83f48\r\nAccess-Control-Expose-Headers: x-bearer-expire-time,x-checkout-refresh-token,x-checkout-access-token-expiration\r\nCache-Control: no-cache\r\nx-powered-by-stack: gateway-2.20.0\r\nx-checkout-refresh-token: undefined\r\nx-checkout-access-token-expiration: undefined\r\nETag: W/\"81-CPDPSao+hW2G30axOq0WVl62cFY:dtagent10263230321103025q7PV\"\r\nServer-Timing: dtSInfo;desc=\"0\", dtRpid;desc=\"-446401736\", dtTao;desc=\"1\"\r\nTiming-Allow-Origin: *\r\nStrict-Transport-Security: max-age=15724800; includeSubDomains\r\nDate: Wed, 14 Jun 2023 09:29:56 GMT\r\nConnection: keep-alive\r\nSet-Cookie: dtCookie=v_4_srv_7_sn_040C437ADAB27B8112C82015754DAD74_perc_100000_ol_0_mul_1_app-3Aea7c4b59f27d43eb_1; Domain=.cluster.local; Path=/\r\nAccess-Control-Allow-Headers: Authorization,Content-Type,Request-Context,Request-Id,X-Requested-With,X-Dior-PCD-SFCC,X-Dior-Frontend-Version,X-Dior-Locale,X-Dior-Preview,X-Dior-Universe,apollographql-client-name,apollographql-client-version,x-dtpc,X-Ctrl-beauty-collection,X-Ctrl-collaboration-page,X-Ctrl-discovery-landing-page,X-Ctrl-frontpage,X-Ctrl-home-collection,X-Ctrl-home-collection-haute-jo,X-Ctrl-home-collection-pap-collection,X-Ctrl-home-pap-collection,X-Ctrl-mcd-collection,X-Ctrl-news-landing-page,X-Ctrl-product-page,X-Ctrl-range-page-cdc,X-Ctrl-range-page-pcd\r\nAccess-Control-Allow-Credentials: true\r\nAccess-Control-Allow-Methods: GET,POST,PUT,PATCH,HEAD,OPTIONS,DELETE\r\nVary: Origin\r\nAccess-Control-Allow-Origin: https://www.dior.com\r\nSet-Cookie: _abck=C3B6F38291E22A635EB62531092DB2C3~0~YAAQDR4gF2ztoI6IAQAAdIU9uQr3obPu4h6/Qj5GE890Tp1VMZwd2O4bVsyybKOsb7suEpSqry6bECGbmUsZccuH3TDWNa5P5uiz32r2jL/03W/SFmeJyRJQIDUokvO47XxUcFBPUYk4KF923uANhI/hliFppomGUgCoaI531SLFoqc9rZkglc2cQQ4+Be3B9U0M/jJOQRu9eaqclwkYrXsiERArDvq88JmxSRqiY49gw5Ao6zGrslBpQeXvaxKGQ5IF+6KXsxiqbd0Mibrjh8+73JxTDNxOFLfyuIzdtKuZKdL/Wyr3o7tv0grwUk6takzwY0zRILheMftJINxwjILq0cbupkuv1s6jWapKAU9/nqa3nAqrxgyF8e/F5MGJXuc8xQGeSBAxZQ3XEtLA0dCsDbk6OEQ=~-1~-1~-1; Domain=.dior.com; Path=/; Expires=Thu, 13 Jun 2024 09:29:56 GMT; Max-Age=31536000; Secure\r\nSet-Cookie: ak_bmsc=519ADB604023F2C705BAE28D92FB0D7C~000000000000000000000000000000~YAAQDR4gF23toI6IAQAAdIU9uRR4Nc9evxTpEmR+r2227rdhqFhaAlS6r4zx2+bxn64rcxxSa/Ds/jCm1attkN7RgCIKqp4CKZPAQQXTGZ91Occhin43CGe1oC1woG52mZYdXlS55FXHu2yCcuyTKMgEHgHk8Z9xx2Daq02oChWluhwhF0NYPHpKwy4WTaDwtFYQLOTIk4dNGUeN7AGKBsznhwQhsmKqfsnV6n3WEt8PPWzjHhdDnMQ67SNpVFFnpcaWYmYNY+irbZRDNnWw3Fg0a8LFFzkWWcQLsco1QiGhf0dAKU5M3+IVcEg7dhMf0zGteGuydYGbhBSB1Ze9fOT83X+nk6TJGaLX0ugj267ZlpwbEBcn867l; Domain=.dior.com; Path=/; Expires=Wed, 14 Jun 2023 11:29:55 GMT; Max-Age=7199; HttpOnly\r\nSet-Cookie: bm_sz=BD4DE7653DF32176DCB2899661FC1081~YAAQDR4gF27toI6IAQAAdIU9uRRSpn3BHxo082ni397EjcdrphjalbUWO7F4rVdHG9avA4a51vHkTyzxsUddYFvhe84jpv3c3SHnfl80E4qNznRtw7dApekZPNx97IYpSExo+Zxxh/NCmn+UbPow6CjlQ3Xo5vaJwp574EA1vR0kJ19t7xt+pqvDZkEk+9jhwOIebRjC6NjSU2aDE5eW/rqcUZjmRl01kx09Vsb5AO0n5nIaXiaiuMbfrDzmOynGh2BD9bxryu4a97a9DcSw+lwwfZgComjO/hY672tIX+fU~3359284~3159352; Domain=.dior.com; Path=/; Expires=Wed, 14 Jun 2023 13:29:55 GMT; Max-Age=14399\r\n\r\n"
            }
        ]
    }
}
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import TlsV1Cracker


cracker = TlsV1Cracker(
    user_token="xxx",
    requests=[{
        "url": "https://www.baidu.com/"
    }, {
        "url": "https://www.baidu.com/"
    }],
)
ret = cracker.crack()
print(ret)
```

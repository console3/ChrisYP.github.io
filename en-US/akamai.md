------
[`Back to homepage`](en.md) 	[`中文文档`](../zh-CN/akamai.md)

## Akamai

### Request URL（POST）:

| Version               | API Endpoint                                                    |
|------------------|---------------------------------------------------------|
| `v2（universal）` | `http://api.nocaptcha.io/api/wanda/akamai/v2` |

### Request Method
- `POST`

### Headers

1. **User-Token**: This is a user-specific key which can be obtained from the main page.
2. **Content-Type**: This should always be set to `application/json`.
3. **Developer-Id**: This is an optional field. For developers, the ID can be fetched from the invite link on the user main page. For example, from the link `xxx/register?c=abcdef`, the developer ID is `abcdef`.

### POST Data (JSON):

The following table details the JSON attributes that should be included in the POST request:

| Parameter  | Type      | Description                                                                                                                                 | Required |
|------------|-----------|---------------------------------------------------------------------------------------------------------------------------------------------|----------|
| href       | String    | The URL of the page that triggered the Akamai verification.                                                                                | Yes      |
| api        | String    | Akamai's endpoint for submitting sensor data. This endpoint can change over time.                                                           | No       |
| telemetry  | Boolean   | Indicates whether the `telemetry` parameter in headers is for verification, e.g., `https://api.maersk.com/` interface's `akamai-bm-telemetry`. Defaults to false. | No       |
| cookies    | Object    | Contains the cookie values returned when requesting the `href`. If `api` is provided, this field is mandatory.                             | No       |
| device     | String    | Defines the device fingerprint type used in the request flow. Values can be "pc" or "mobile". Defaults to "mobile".                        | No       |
| internal   | Boolean   | Specifies whether the verification process uses a domestic proxy. Defaults to true.                                                         | No       |

Under the `cookies` object:

| Parameter | Type          | Description                                                  | Required |
|-----------|---------------|--------------------------------------------------------------|----------|
| value     | String/Object | Can be in string format or key-value pairs. Must include `_abck` and `bm_sz`.           | No       |
| uri       | String        | Usage address for cookies. This is typically the same as `href`.                         | No       |

### Response Data (JSON):

For the case where the submission is true (`submit=true`):

| Parameter      | Type      | Description                                                         |
|----------------|-----------|---------------------------------------------------------------------|
| status         | Integer   | Indicates if the call was successful. 1 for success, 0 for failure. |
| msg            | String    | Descriptive message in Chinese indicating the result of the call.   |
| id             | String    | Unique ID for the request, useful for subsequent query records.      |
| data._abck     | String    | Returns the valid `_abck` cookie when verification passes.           |
| cost           | String    | Time taken for verification, in milliseconds.                        |

A successful response example:
```json
{
	"status": 1,
	"msg": "验证通过",
	"id": "8a8f0778-da09-4eea-a32d-e3b508654ba6",
	"cost": "1984.57ms",
	"data": {
		"_abck": "2EDD22DB758F24695963..."
	}
}
```

### Use Cases:
The API seems to be designed for multiple use cases, including:
1. **Basic URL Verification**: Just sending the `href` to check if it triggers an Akamai challenge.
2. **Detailed Verification with Cookies**: Submitting `href` along with cookies obtained from the previous response. This might be needed if the Akamai challenge changes its API endpoint frequently.
3. **Device-Specific Verification**: By specifying the device type, users can get responses as they would appear on mobile or PC devices.
4. **Telemetry Verification**: Some services, like Maersk, might have a different type of Akamai challenge that involves telemetry.

In practice, users would likely start with the basic URL verification, and if that fails or if they need a more specific kind of verification, they'd include additional parameters in the request.

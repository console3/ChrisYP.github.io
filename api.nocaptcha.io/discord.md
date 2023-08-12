------
[`返回首页`](../README.md)    [`上一页`](tls.md)

## Discord

### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `group（加群）` | `http://api.nocaptcha.io/api/wanda/discord/group` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| `authorization`           | `String`  | `账号登录凭证`                                                                                                                          | `是` |
| `group_ip`        | `String`  | `加群的 id`       | `否` |
| `cookies.value` | `String or Object` | `请求流程使用的 cookies, 可以是字符串或对象, { '1': '2', '3': '4' } / '1=2; 3=4'`   | `否` |
| `cookies.uri`   | `String`  | `请求流程的 cookie set 的域名, 使用 url 即可`   | `否` |
| `proxy`         | `String`  | `请求流程使用的代理, 支持 protocol: http/https/socks5, 无验证代理格式: {ip}:{port}, 有验证代理格式: {user}:{password}@{ip}:{port}, socsk5 代理需要加上代理协议: {protocol}://{ip}:{port}`   | `否` |

#### json 示例

```
{
    "authorization": "MTExNzI1NDQ3NzA2NjU0MzE5NQ.xxxxxx",
    "group_id": '645607528297922560',
}
```

### Response Data（JSON）:

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data`         | `String`  | `加群结果`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
    "status": 1,
    "msg": "验证成功",
    "id": "049bfae2-4e84-4f29-99aa-a33688991355",
    "cost": "18809.89ms",
    "data": `{"id":"645607528297922560","name":"The Forbidden Trove","icon":"a_c177897c1751abde48b893844811a1a7","description":"The largest server for everything Path of Exile related. Join for our trading hub, help rooms, socializing & much more!","home_header":null,"splash":"cb8c8d1f10b15932154f8e23f717e9f9","discovery_splash":"eedcef7392c2549f9be77e527ff67e27","features":["ENABLED_DISCOVERABLE_BEFORE","DISCOVERABLE","THREADS_ENABLED","TEXT_IN_VOICE_ENABLED","VIP_REGIONS","BANNER","GUILD_WEB_PAGE_VANITY_URL","SOUNDBOARD","ROLE_ICONS","PARTNERED","GUILD_ONBOARDING_EVER_ENABLED","AUTO_MODERATION","PREVIEW_ENABLED","NEW_THREAD_PERMISSIONS","NEWS","MEMBER_PROFILES","SEVEN_DAY_THREAD_ARCHIVE","PRIVATE_THREADS","RELAY_ENABLED","GUILD_HOME_TEST","WELCOME_SCREEN_ENABLED","VANITY_URL","ANIMATED_BANNER","INVITE_SPLASH","ANIMATED_ICON","THREE_DAY_THREAD_ARCHIVE","GUILD_ONBOARDING_HAS_PROMPTS","COMMUNITY","GUILD_ONBOARDING","CHANNEL_ICON_EMOJIS_GENERATED"],"welcome_screen":{"description":"A community of PoE enthusiasts, offering safe trading services and crafting powerful items.","welcome_channels":[{"channel_id":"669127045678104587","description":"Read the rules!","emoji_id":"737218162822610994","emoji_name":"tft"},{"channel_id":"667298412596559904","description":"Everything we do here, at a glance","emoji_id":"737218162822610994","emoji_name":"tft"},{"channel_id":"664055576568791062","description":"Get help on a build and discuss builds","emoji_id":null,"emoji_name":"🔧"},{"channel_id":"664772968328462336","description":"Get help from experienced crafters","emoji_id":null,"emoji_name":"🛠️"},{"channel_id":"666519736007262240","description":"Chat about anything PoE","emoji_id":null,"emoji_name":"💬"}]},"emojis":[{"name":"PepeHands","roles":[],"id":"661789254623428644","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"Pepega","roles":[],"id":"661789573940117537","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"KEK","roles":[],"id":"661789881223348224","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"monkaS","roles":[],"id":"662662847288967179","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"wut","roles":[],"id":"662668570110590976","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"LULW","roles":[],"id":"662670461557014550","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"feelsBadMan","roles":[],"id":"662670462178033664","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"notBad","roles":[],"id":"662670462198874132","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"OMEGALUL","roles":[],"id":"662670462215782440","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pogU","roles":[],"id":"662670462538612746","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepeLaugh","roles":[],"id":"662670462538743818","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"vaal","roles":[],"id":"662672102330990624","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"monkaW","roles":[],"id":"662672102561677319","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"yoink","roles":[],"id":"662672102595231765","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"nice","roles":[],"id":"662672102687637504","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"POGHYPE","roles":[],"id":"662877258947756033","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"cringe","roles":[],"id":"664308307955154976","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepegaHands","roles":[],"id":"664665340424486926","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"AlphasHowl","roles":[],"id":"664665712115056640","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"headhunter","roles":[],"id":"664666062628847616","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"weSmart","roles":[],"id":"664713673981296650","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepeHyper","roles":[],"id":"665787165351084043","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"pepeGun","roles":[],"id":"665787165568925696","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"weebsOut","roles":[],"id":"665787165585702923","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepeYikes","roles":[],"id":"666391735118594058","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"LaughPointPeepo","roles":[],"id":"666522537748070413","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"feelsAmazingMan","roles":[],"id":"666523119388721168","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"madRage","roles":[],"id":"666523749486690314","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"peepoPing","roles":[],"id":"666523749595480074","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepeKawaii","roles":[],"id":"666544459567202306","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"voteYes","roles":[],"id":"666544459605082142","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"voteNo","roles":[],"id":"666544459680317440","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"ex5k","roles":[],"id":"666687729496621079","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"brokenTennisBallOrb","roles":[],"id":"666688385175519243","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"Chris","roles":[],"id":"666689332740096020","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"Annul","roles":[],"id":"666691309146210304","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"divine","roles":[],"id":"666765844541603861","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"hidethepain","roles":[],"id":"667788392666497035","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"happyPeepo","roles":[],"id":"685178795355144239","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"homer","roles":[],"id":"711365619508969564","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"pins","roles":[],"id":"713457366628040854","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"popcorn","roles":[],"id":"716800572820422778","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"sadKEK","roles":[],"id":"717804265929834647","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"POGSLIDE","roles":[],"id":"717804266101801012","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"pog","roles":[],"id":"718917896004173885","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"kreygasm","roles":[],"id":"722148644404330607","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"mirror2","roles":[],"id":"722150395270397992","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"monkaWhat","roles":[],"id":"722152503956733994","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepeMeltdown","roles":[],"id":"722152504300797984","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"thisisfine","roles":[],"id":"722152573213212713","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"5Head","roles":[],"id":"722152609904984171","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"happyPeepoFarmer","roles":[],"id":"722153641619751023","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"peepoBlanket","roles":[],"id":"722154655311855709","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"PepegaBlind","roles":[],"id":"722155098259718194","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepegaHunter","roles":[],"id":"722155477781446697","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"4Head","roles":[],"id":"722155879310426202","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"pepegaHype","roles":[],"id":"722156594170822676","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"doubt","roles":[],"id":"722165413454283013","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"patpat","roles":[],"id":"722172759580344426","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"whyme","roles":[],"id":"722172810658578442","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"peepoSimp","roles":[],"id":"722575757167165471","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"regret","roles":[],"id":"723552590796685323","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"goosePls","roles":[],"id":"728816782881587212","require_colons":true,"managed":false,"animated":true,"available":true},{"name":"illuminati","roles":[],"id":"729882690115076147","require_colons":true,"managed":false,"animated":false,"available":true},{"name":"stonks","roles":[],"id":"731319844984'... 76225 more characters`,
}
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import TlsV1Cracker


cracker = DiscordCracker(
    user_token="xxx",
    authorization="MTExNzI1NDQ3NzA2NjU0MzE5NQ.GZoD5U.xxx",
    group_id='645607528297922560',
    debug=True
)
ret = cracker.crack()
print(ret)
```

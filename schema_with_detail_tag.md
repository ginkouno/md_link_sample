## The table of contents

- <a href="#resource-shop">Shop</a>
  - <a href="#shop-shop-search-api">GET /api/shops</a>
  - <a href="#shop-店舗情報詳細-api">GET /api/shops/{shop_id}</a>

## <a name="resource-shop">Shop</a>

Stability: `prototype`

ShopInformationAPI

### Attributes

<details>

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **address** | *string* | Shop Address | `"Ginza Tokyo"` |
| **id** | *integer* | Shop ID | `42` |
| **latitude** | *string* | Shop latitude | `"35.695192"` |
| **longitude** | *string* | Shop longitude | `"139.758681"` |
| **name** | *string* | Shop Name | `"Ultimate Sushi Shop"` |

</details>

### <a name="link-GET-shop-/api/shops">Shop Shop Search API</a>

<details>

Shop search by geocode

```
GET /api/shops
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **latitude** | *string* | ユーザの現在位置(緯度) | `"35.695192"` |
| **longitude** | *string* | ユーザの現在位置(経度) | `"139.758681"` |


#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **name** | *string* | 中間一致 | `"幸"` |


#### Curl Example

```bash
$ curl -n https://api.yasu.com/api/shops
 -G \
  -d name=%E5%B9%B8 \
  -d latitude=35.695192 \
  -d longitude=139.758681
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 42,
    "name": "Ultimate Sushi Shop",
    "address": "Ginza Tokyo",
    "latitude": "35.695192",
    "longitude": "139.758681",
    "distance": 312
  }
]
```

</details>

### <a name="link-GET-shop-/api/shops/{(%23%2Fdefinitions%2Fshop%2Fdefinitions%2Fid)}">Shop 店舗情報詳細 API</a>

<details>

Provide shop detail information

```
GET /api/shops/{shop_id}
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **latitude** | *string* | search area latitude | `"35.695192"` |
| **longitude** | *string* | search area longitude | `"139.758681"` |


#### Curl Example

```bash
$ curl -n https://api.yasu.com/api/shops/$SHOP_ID
 -G \
  -d latitude=35.695192 \
  -d longitude=139.758681
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 42,
  "name": "Ultimate Sushi Shop",
  "address": "Ginza Tokyo",
  "latitude": "35.695192",
  "longitude": "139.758681",
  "holiday": "Sunday",
  "business_hours": "11:00-26:30(LO 26:00)",
  "distance": 312
}
```

</details>


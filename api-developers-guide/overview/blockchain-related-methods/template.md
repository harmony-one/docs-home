# Template

{% api-method method="post" host="http://l0.b.hmny.io:9500" path="" %}
{% api-method-summary %}
hmy\_getBalance
{% endapi-method-summary %}

{% api-method-description %}
Gets a Balance for a users public address
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=false %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="address" type="string" required=true %}
Address represents the 20 byte address of a Harmony Account. e.g.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"0x59569805f677af800"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Sample Curl Command

```text
curl http://s0.b.hmny.io:9500 -H "Content-Type: application/json" -X POST --data '{"jsonrpc":"2.0","method":"hmy_getBalance","params":["0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", "latest"],"id":1}'
```


---
description: Отправка данных о количестве серверов и шардов.
---

# SDC Bots

{% swagger method="post" path="/bots/:id/stats" baseUrl="https://api.server-discord.com/v2" summary="Send bot data" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" required="true" name="id" type="String" %}
Айди бота
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
SDC Token
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="servers" type="Number" %}
Количество серверов, не менее 1
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="shards" type="Number" %}
Количество шардов, не менее 1
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Данные успешно установлены" %}
```javascript
{
  "status": true
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Пропущен требуемый параметр" %}
```json
{
  "error": {
    "msg": "<parameterName> parameter is missing",
    "type": "MISSING_<parameter_name_snake_case>",
    "code": 400
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Не правильно передан параметр" %}
```json
{
  "error": {
    "msg": "<parameterName> parameter is invalid",
    "type": "INVALID_<parameter_name_snake_case>",
    "code": 400
  }
}
```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Нет доступа" %}
```json
{
  "error": {
    "msg": "You do not have access to this action",
    "type": "FORBIDDEN_ACTION",
    "code": 403
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Бот не найден" %}
```json
{
  "error": {
    "msg": "<parameterName> entity not exist",
    "type": "DOES_NOT_EXIST_<entity>",
    "code": 404
  }
}
```
{% endswagger-response %}
{% endswagger %}

### Ограничения

{% hint style="danger" %}
Вы не можете делать больше 2 запросов за 1 минуту.
{% endhint %}

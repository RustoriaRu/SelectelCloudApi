# SelectelCloudApi
api select cloud api 

api method https://support.selectel.ru/storage/api_info/

## Exemple
Получаем список доступных контейнеров пользоватея
```python
from selectel_cloud_api import ApiSelectelCloud

api = ApiSelectelCloud(user='name', password='pass')

response = api.get(params={'format': 'json'})

print(response.json())
```
Ответ: `[{u'count': 0, u'name': u'name', u'rx_bytes': 0, u'bytes': 0, u'tx_bytes': 0, u'type': u'public'}]`

---

Пример получения информации по контейнеру
```python
response = api.container_name.head()

print(response.headers)
```
---

Удаление контейнера
```python
response = api.container_name.delete()

print(response.status_code)
```
* 204 (No Content) - при успешном удалении
* 404 (Not Found) - указанный контейнер не существует
* 409 (Conflict) - ошибка удаления, контейнер не пустой

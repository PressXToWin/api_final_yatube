# api_final

API для социальной сети блогеров YaTube. Позволяет читать записи и комментарии. Для зарегистрированных пользователей доступен функционал добавления новых записей и комментариев, а также подписка на понравившихся авторов.

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/PressXToWin/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```

## Примеры запросов:

### Получить аутентификационный токен:

```
POST http://127.0.0.1:8000/api/v1/jwt/create/
```

В `data` передаются аутентификационные данные:

```json
{
  "username": "string",
  "password": "string"
}
```

### Получить список постов:

```
GET http://127.0.0.1:8000/api/v1/posts/
```

Пример ответа:

```json
[
    {
        "id": 1,
        "author": "admin",
        "text": "text",
        "pub_date": "2023-01-01T00:00:00.000000Z",
        "image": null,
        "group": null
    }
]
```

### Создать новый пост

В заголовке запроса обязательно указать `Authorization`:`Bearer <токен>`.

```
POST http://127.0.0.1:8000/api/v1/posts/
```

В `data` передать обязательное поле `text`:

```json
{
    "text": "text"
}
```

Пример ответа:

```json
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2023-01-01T00:00:00.000000Z",
    "image": "string",
    "group": 0
}
```

С документацией к остальным запросам можно ознакомиться по адресу

```
http://127.0.0.1:8000/redoc/
```
# API Yatube

### Описание
Благодаря этому проекту вам доступно:

- Посты
1) Получение списка постов. При указании параметров limit и offset выдача работает с пагинацией.
2) Получение поста по id.
2) Создание и изменение постов(доступно только авторизованным пользователям, изменение чужих постов недоступно)
3) Удаление своих посты

- Комментарии
1) Получение всех комментариев к публикации.
2) Добавление нового комментария к публикации. Анонимные запросы запрещены.
3) Получение комментария к публикации по id.
4) Обновление комментария к публикации по id. Обновить комментарий может только автор комментария.
5) Удаление комментария к публикации по id. Доступно только автору комментария.

- Сообщества
1) Получение списка доступных сообществ.
2) Получение информации о сообществе по id.

- Подписки
1) Получение информации о подписках пользователя, сделавшего запрос. Анонимные запросы запрещены.
2) Подписка на конкретного автора.

### Технологии
Python 3.7  
Django 2.2.16  
Django REST framework 3.12  
Djoser 2.1.0  

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Rodion-dot-com/api_final_yatube.git
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

### Примеры запросов:

Получение публикаций:

```
GET http://127.0.0.1:8000/api/v1/posts/?limit=2

Response:
{
    "count": 7,
    "next": "http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=2",
    "previous": null,
    "results": [
        {
            "id": 1,
            "author": "rodion",
            "text": "string",
            "pub_date": "2022-10-13T16:09:56.383533Z",
            "image": "http://127.0.0.1:8000/posts/temp.png",
            "group": null
        },
        {
            "id": 2,
            "author": "rodion",
            "text": "string1",
            "pub_date": "2022-10-14T08:16:37.222283Z",
            "image": null,
            "group": null
        }
    ]
}
```

Создание публикации:
```
POST http://127.0.0.1:8000/api/v1/posts/

Body:
{
    "text": "string",
    "image": "string",
    "group": 0
}

Response:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}
```

Добавление комментария:
```
POST http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/

Body:
{
    "text": "string"
}

Response:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
}
```

Подписки:
```
GET http://127.0.0.1:8000/api/v1/follow/

Response:
[
    {
        "user": "string",
        "following": "string"
    }
]
```

### Автор:
Прошляков Родион  
https://github.com/Rodion-dot-com

Развертка приложения
--------------------

Сначала необходимо создать папку `env`, в которой будет размещаться виртуальное окружение для проекта. Проект создавался с использованием <b>Python</b> версии <b>3.8</b>.

Дальше, установить виртуальное окружение в этой папке:

`python -m venv env/myshop`

И активировать, при помощи, `env\myshop\Scripts\activate.bat` на Windows, и `env/myshop/Scripts/activate` на Linux.

Следующий шаг, установка всех необходимых модулей.

```
pip install Django==3.0.*
pip install Pillow==7.0.0
```

Для работы следующих модулей необходимо установить [Erlang](https://www.erlang.org/downloads) и [RabbitMQ](https://www.rabbitmq.com/download.html).

```
pip install celery==4.4.2
pip install flower==0.9.3
```

Для симуляции реальных транзакций, в проекте используется [Braintree Sandbox](https://sandbox.braintreegateway.com). Следующий модуль позволяет организовать взаимодействие с этим сервисом.

`pip install braintree==3.59.0`

После регистрации на этом сервисе, необходимо заменить ключи в файле проекта `myshop/settings.py` на свои.

```
BRAINTREE_MERCHANT_ID = 'qtr7xq7r9cz3crfd'
BRAINTREE_PUBLIC_KEY = 'j7nng38kjm66mrpq'
BRAINTREE_PRIVATE_KEY = 'XXXX'
```

Вместо XXXX - ваш приватный ключ. В данном случае он отсутствует, в целях безопасности.

На Windows, для установки следующего модуля, может понадобиться [Microsoft Visual C++ Build Tools](https://visualstudio.microsoft.com/ru/downloads).

`pip install weasyprint==51`

Установка расширений для Django.

```
pip install django-rosetta==0.9.3
pip install django-parler==2.0.1
pip install django-localflavor==3.0.1
```

Для работы следующего модуля необходимо установить [Redis](https://redis.io/). В случае Windows, необходимо поставить службу [redis.msi](https://github.com/microsoftarchive/redis/releases)

`pip install redis==3.4.1`

После установки всех модулей, необходимо запустить проект.

1. В случае инициализации с нуля.

```
python manage.py migrate
python manage.py createsuperuser
```

2. В случае использование заготовки.

Материалы заготовки находятся в папке "For test". Необходимо скопировать все из этой папки в папку с проектом в `myshop`.

Теперь, запуск сервера при помощи `python manage.py runserver`. Перейти к приложению можно по этой ссылке [http://127.0.0.1:8000](http://127.0.0.1:8000)

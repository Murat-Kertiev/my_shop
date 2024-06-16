## Онлайн магазин - MyShop

---

## О проекте

Проект MyShop - это интернет-магазаин, который предоставляет клиентам возможность просматривать товары, добавлять их в корзину, применять коды скидок, проходить процесс оформления платежа, оплачивать кредитной картой и получать счета-фактуры. <br> Реализован рекомендательный механизм, чтобы рекомендовать товары своим клиентам. <br> MyShop интернационализирван и предлагает свои товары на нескольких языках.'

### **Подготовка проекта к запуску:**

Клонировать репозиторий и перейти в него в командной строке:

> git clone git@github.com:Murat-Kertiev/my_shop.git
> 
> cd my_shop

Cоздать и активировать виртуальное окружение:

> python -m venv venv
> 
> source venv/scripts/activate

Установить зависимости из файла requirements.txt:

> python -m pip install --upgrade pip
> 
> pip install -r requirements.txt

Выполнить миграции:

> python manage.py migrate

Создать суперюзера (root):

> python manage.py createsuperuser

## Запустить проект:

Скачайте образы с DockerHub:


> docker pull rabbitmq
> 
> docker pull redis

Следующие команды выполняйте каждую в отдельном терминале.

> python3 manage.py runserver
> 
> docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:management
> 
> celery -A my_shop worker -l info
> 
> docker run -it --rm --name redis -p 6379:6379 redis
> 
> stripe listen --forward-to localhost:8000/payment/webhook/

Запустится проект и будет доступен по адресу [localhost:8000](http://localhost:8000/).
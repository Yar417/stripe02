# stripe02
Проект построен на Django + Stripe (платежная система) 

1) Создание простого приложения Django 
  - модель Item с ценой, описанием, названием (отображаются в админке)
  - вывод всех товаров через ListView на главной странице ( home.html)
  - через DetailView на отдельный html(item/{id}) организован вывод товаров по их ID из базы данных, здесь же кнопка для перехода в сервис оплаты Stripe (item.html)
  - 2 html для обратного редиректа (success.html, cancel.html)

2) Подключение функционала Stripe
  - в settings.py находятся два ключа от Stripe ( секретный и публичный) и домен главной страницы для обратного редиректа при успешной/неуспешной оплате.
  - две функции в файле views.py: 
    - create_checkout_session отправляет Json с информацией о товаре(имя, цена, описание) в кнопку для перехода на Stripe
    - stripe_config - отправляет публичный ключ
3) Методология работы: 
  - выбираем один из товаров на Главной странице (кнопка "Read more and buy")
  - страница товара с описанием и переходом к оплате (единственная кнопка) 
  - шаблонизатор передает в скрипт кнопки ID товара (пришлось выводить sctipt именно на странице item.html, а не в отдельном файле .js) 
  - срабатывает функция create_checkout_session, создает редирект на страницу Stipe для оплаты
  - при успешной оплате пользователя возвращает на сайт с уведомлением об успешном заказе

4) Для публикации решения использовал виртуальный сервер(vps)
 - Ubuntu 22.04 - ос
 - Vmmanager - панель управления сервером
 - Доступ к серверу по ключу ssh, через PuttY
 - Gunicorn -  WSGI-сервер
 - Nginx - HTTP-сервер и обратный прокси-сервер
 Деплой производил вручную, без сторонних скриптов.


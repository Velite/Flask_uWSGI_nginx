# Flask_uWSGI_nginx

Настройка сервера:
1. Обновляемся: sudo apt-get update
2. Ставим утилиты: sudo apt-get install nginx-full uwsgi uwsgi-plugin-python3 python3-pip, возможно ещё: python3 python3-dev python3-setuptools - возможно, нужно будет дополнить список репозиториев, чтобы был доступен uwsgi
3. Устанавливаем инструменты для виртуального окружения: sudo pip3 install virtualenv или sudo easy_install-3.4 virtualenv
4. Создаём папку для проекта
5. Заходим в неё и настраиваем виртуальное окружение: virtualenv <имя_папки_для_вирт_среды>
6. Активируем окружение: source /<папка_проекта>/<папка_вирт_среды>/bin/activate
7. Находясь в вирт. среде ставим инструменты: pip3 install flask, после этого выходим через deactivate
8. В папке проекта создаём файл проекта, например app.py, не называть flask.py!
9. В созданном файле набиваем простой тестовый код flask
10. Заходим в папку /etc/nginx/sites-available
11. Создаём новый конфиг, например <a href="https://raw.githubusercontent.com/Velite/Flask_uWSGI_nginx/master/flask.conf">flask.conf</a>
12. Создаём для него символическую ссылку в папке sites-enabled: sudo ln -s /etc/nginx/sites-available/flask.conf /etc/nginx/sites-enabled/flasc.conf
13. Если имеется символическая ссылка типа default, то удаляем её: sudo rm /etc/nginx/sites-enabled/default
14. Заходим в папку /etc/uwsgi/apps-available и создаём там новый файл, например flask.ini или flask.json - проверить права на папки/файлы/сокет
15. Делаем символическую ссылку в папку apps-enabled по аналогии с п.12
16. Перезапускаем uwsgi и nginx: sudo service restart uwsgi или sudo service uwsgi start/stop
17. Проверяем в браузере результат по адресу нашего сервера

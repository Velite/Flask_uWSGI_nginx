# Flask_uWSGI_nginx

<h3>Настройка сервера:</h3>
<ol>
  <li>Обновляемся:<pre>sudo apt-get update</pre></li>
  <li>Ставим утилиты:<pre>sudo apt-get install nginx-full uwsgi uwsgi-plugin-python3 python3-pip</pre>возможно ещё:<pre>python3 python3-dev python3-setuptools</pre>возможно, нужно будет дополнить список репозиториев, чтобы был доступен uwsgi</li>
  <li>Устанавливаем инструменты для виртуального окружения:<pre>sudo pip3 install virtualenv или sudo easy_install-3.4 virtualenv</pre></li>
  <li>Создаём папку для проекта</li>
  <li>Заходим в неё и настраиваем виртуальное окружение:<pre>virtualenv <имя_папки_для_вирт_среды></pre></li>
  <li>Активируем окружение:<pre>source /<папка_проекта>/<папка_вирт_среды>/bin/activate</pre></li>
  <li>Находясь в вирт. среде ставим инструменты:<pre>pip3 install flask</pre>после этого выходим через<pre>deactivate</pre></li>
  <li>В папке проекта создаём файл проекта, например <a href="https://raw.githubusercontent.com/Velite/Flask_uWSGI_nginx/master/app.py">app.py</a>, <strong>не называть flask.py!</strong></li>
  <li>В созданном файле набиваем простой <a href="https://raw.githubusercontent.com/Velite/Flask_uWSGI_nginx/master/app.py">тестовый код flask</a></li>
  <li>Заходим в папку /etc/nginx/sites-available</li>
  <li>Создаём новый конфиг, например <a href="https://raw.githubusercontent.com/Velite/Flask_uWSGI_nginx/master/flask.conf">flask.conf</a></li>
</ol>
 
12. Создаём для него символическую ссылку в папке sites-enabled: sudo ln -s /etc/nginx/sites-available/flask.conf /etc/nginx/sites-enabled/flask.conf
13. Если имеется символическая ссылка типа default, то удаляем её: sudo rm /etc/nginx/sites-enabled/default
14. Заходим в папку /etc/uwsgi/apps-available и создаём там новый файл, например <a href="https://raw.githubusercontent.com/Velite/Flask_uWSGI_nginx/master/flask.ini">flask.ini</a> или <a href="https://raw.githubusercontent.com/Velite/Flask_uWSGI_nginx/master/flask.json">flask.json</a> - проверить права на папки/файлы/сокет
15. Делаем символическую ссылку в папку apps-enabled по аналогии с п.12
16. Перезапускаем uwsgi и nginx: sudo service restart uwsgi или sudo service uwsgi start/stop
17. Проверяем в браузере результат по адресу нашего сервера

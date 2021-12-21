# teams-bot

Simple Q&amp;A bot for Microsoft Teams

### TO-DO
       
- [ ] add backend database (postgresql)
- [ ] deploy bot in azure cloud
- [ ] http routing for deeppavlov bert
- [ ] add messaging system (kafka)
- [ ] improve functionality
- [ ] documentation to functions

# guide

Необходимо установить и настроить pyenv , чтобы иметь возможность
переключаться между различными версиями Python (нужно для установки
DeepPavlov, так как не поддерживает Python 3.8).

Ниже приведены инструкции по
запуску чат-бота на локальной машине:

1. Активировать виртуальную среду:

       virtualenv env; \
       source ./env/bin/activate; \

2. Установить библиотеку DeepPavlov, загрузить данные модели:

       pip install deeppavlov; \
       python3 -m deeppavlov install squad_bert; \
       python3 -m deeppavlov download squad_bert; \

3. Запустить REST-сервер с моделью:

       python3 -m deeppavlov riseapi squad_bert -p 5005

4. Скопировать непосредственно репозиторий с проектом:

       git@github.com:rcreator/teams-bot.git

5. Установить все необходимые зависимости:
        
       pip install -r requirements.txt
 
7. Запустить хост для бота:

       python3 app.py

7. Подключиться к боту через Bot Framework Emulator:

       Bot URL = http://localhost:3978/api/messages

Протестировать специфичную для Teams функциональность (например,
приветствие при добавлении в команду / канал), можно только имея подписку
Azure (доступен бесплатный период). Инструкция по запуску чат-бота в Microsoft
Teams:

8. Создать туннель между локальной машиной и каналом Microsoft Teams:
       
       ngrok http -host-header=rewrite 3978

9. Обновить файл config.py с настройками чат-бота:

       APP.ID = “<your bot framework registration id>”
       APP.PASSWORD = “<your bot framework registration secret>”

10. Установить все необходимые зависимости:
       
        pip install -r requirements.txt

11. Запустить веб-сервер для бота:

        python3 app.py

12. Заменить все вхождения <<YOUR-MICROSOFT-APP-ID>> на ваш
идентификатор приложения в файле “manifest.json”Загрузите manifest.zip в
Teams (в представлении «Приложения» нажмите «Загрузить
настраиваемое приложение»)
  
13. Загрузить zip-архив “manifest.zip” с файлами, лежащими в папке
“teams_app_manifest”, в “Apps” (“Upload a custom app”)

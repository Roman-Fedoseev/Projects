Проект "Синонимайзер экономических терминов" выполнен совместно с https://github.com/Vladislav0802 
Это веб-сервис на базе Streamlit и ngrok, использующий модель QVikhr-2.5-1.5B для автоматического упрощения сложных финансовых и экономических определений до уровня 10-11 класса. Через промт-инжиниринг модель настраивалась на замену профессиональной лексики простыми словами без искажения смысла, а готовая модель хранится локально в Google Drive для быстрой загрузки. Сервис позволяет пользователям вводить сложные термины и мгновенно получать их понятные формулировки.

Как развернуть у себя синонимайзер?
1) Заходим на сайт https://ngrok.com (Может понадобиться VPN, я использовал Hola VPN)
Регистрируемся (я делал это через Google-аккаунт), переходим на вкладку Your Authtoken, 
нажимаем на иконку глаза - это ваш токен, который нужно будет скопировать и вставить в код дальше.
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/token_ngrok.jpg

2) Загружаем себе в Colab файл Synonymizer и requirements.txt
ВНИМАНИЕ! Здесь стоит оговориться, что requirements.txt желательно запускать в виртуальной среде, что б не перезаписывать версии ваших библиотек. Выполнение данного шага мы оставляем на ваше усмотрение.

3) Открываем файл, запускаем строчки кода в самом верху (установка зависимостей через requirements.txt) 
один раз запускаем код из блока "Блоки кода ниже запускаются в первую очередь и один раз" (Это нужно для скачивания модели, она будет помещена на ваш диск), 
далее эти строки кода можно закомментировать, что б не запускать их лишний раз.
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/one_time_block.jpg

4) Скопированный код из пункта 1) помещаем вместо звездочек как показано на скрине:
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/stars.jpg

5) Запускаем весь код КРОМЕ ПОСЛЕДНЕГО БЛОКА КОДА (последний блок кода используется для прерывания соединения с веб-сервисом, смотреть картинку)
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/end_processes.jpg

Мы закомментировали его на всякий случай, что б вы его случайно не запустили при первом запуске.

Что происходит в этот момент: сначала вы дадите доступ колабу к своим файлом, что б он мог прочитать ваш диск. Далее идет установка зависимостей через requirements.txt
Далее копируется модель с диска в вашу среду Colab, которую вы скачали ранее (помните тот код, что запускается один раз? Это оно и есть).
Установится соединение с ngrok (вы же вставили свой токен в нужное место, верно?).
Создастся файл с кодом, нужным для самого веб-сервиса.

6) Далее вы увидите следующее сообщение:
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/link_web.jpg

Смело переходим по ссылке (ПО ПЕРВОЙ ССЫЛКЕ, А НЕ ПО ТОЙ, ЧТО ИМЕЕТ ВИД localhost8501)

7) Выскочит предварительное окно, нужно будет нажать Visit Site
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/Visit_site.jpg

8) Веб-сервис начнет свою загрузку, вы увидете следующее окно:
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/loading_web.jpg

9) Далее откроется сам веб-сервис:
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/load_web.jpg

Если суммаризировать, то в файле Final-model-web-version можно просто запустить все ячейки, дать доступ к диску и подождать пока произойдет установка зависимостей, скачивание модели и т.д. Далее просто тапнуть на ссылку, ведущую на веб-сервис и пользоваться.

Инструкция по использованию:
В окно ввода определения вы помещаете текст, который нужно упростить, а затем нажимаете кнопку "Упростить".
Модель будет работать изначально на CUSTOM_PROMPT (Это тот промпт, что мы настраивали для корректной работы модели).
При желании можно сбросить промпт к дефолтному (Это промпт с сайта Transformers, без преднастройки). Чтобы это сделать нажмите Сбросить к "SYSTEM_PROMPT".
Чтобы вернуть кастомный промпт, нажмите кнопку Сбросить к "CUSTOM_PROMPT".
Если вы хотите поэкспериментировать с настройкой собственного промпта, то нажмите "Настройка системного промпта".

Итак, модель выдает вам упрощенный текст.
Чуть ниже, если пролистать, можно увидеть метрики ответа модели (SBERT и Индекс удобочитаемости Флеша для ru).
Еще чуть ниже есть история всех ваших запросов, можно открыть шторку и посмотреть подробнее каждый прошлый запрос. Историю можно очистить по одноименной кнопке.
Также в самом конце есть кнопка, через которую можно скачать PDF-файл с историей ваших запросов.
https://raw.githubusercontent.com/Roman-Fedoseev/Projects/main/Synonymizer_pet_project/images/metrics_and_history.jpg






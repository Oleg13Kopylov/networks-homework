# Общая информация

В папке Kopylov_Oleg_hw2 лежит Dockerfile и папка app, в которой находится скрипт на bash. Скрипт называется Kopylov_Oleg_script_for_MTU.

В нем с помощью бинарного поиска находится требуемое MTU. Для удобства пользователя выводятся логи. Это происходит, если задан корректный host.

Если же host задан некорректно и в принципе не отвечает на пинги, то бинарный поиск не запускается, пользователю выводится сообщение о том, что хост некорретный, и программа завершается.

Примеры корректных хостов: google.com, apache.org, ok.ru

Пример некорректного хоста: 11.com

# Запускать нужно так:

Скачать папку Kopylov_Oleg_hw2. Например, качать zip-архив этой папки можно по ссылке https://download-directory.github.io/?url=https%3A%2F%2Fgithub.com%2FOleg13Kopylov%2Fnetworks-homework%2Ftree%2Fmain%2Flab2%2FKopylov_Oleg_hw2 . Разахивировать скачанный архив.

Зайти в терминал и перейти в папку Kopylov_Oleg_hw2 (при способе скачивания через ссылку выше эта папка будет называться Oleg13Kopylov networks-homework main lab2-Kopylov_Oleg_hw2). Затем написать в терминале две команды:

1) docker build -t other_hw2_calc_mtu .

2) docker run other_hw2_calc_mtu **apache.org**

**Во второй команде вместо apache.org можно ввести любой другой хост. Так пользователь может определять min MTU до разных хостов.**

# Пример работы
В файле output_correct_host.txt пример вывода программы при корректном хосте apache.org

В файле output_invalid_host.txt пример вывода программы при некорректном хосте 11.com

Ниже представлен скриншот, на котором видно результаты выполенения программы сначала для apache.org, а затем для 11.com (Для apache.org результат не помещается на скриншот полностью; весь вывод представлен в файле output_correct_host.txt).

**Скриншот**

<img width="1440" alt="Screenshot 2022-12-05 at 16 31 33" src="https://user-images.githubusercontent.com/55313421/205649387-bb998955-b3dc-45e3-91c7-dba58995e3d4.png">

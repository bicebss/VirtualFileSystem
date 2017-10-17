# VirtualFileSystem

Виртуальный файловый сервер/клиент. Состоит из двух частей: сервера и клиента.

## Сервер

Сервер обрабатывает запросы клиентов для работы с виртуальной файловой системой (ВФС): создание, удаление, перемещение и копирование файлов и директорий. Все клиенты работают с одной и той же ВФС, сервер обеспечивает синхронизацию работы. Когда один из клиентов делает изменения в ВФС (например, создает новый файл), остальные клиенты получают уведомление об изменениях.

## Клиент

Клиент представляет собой консольное JAVA приложение, которое позволяет работать с сервером из командной строки.

Разрешенные команды:
* Сonnect server_name[:port] UserName - соединение с сервером. После вызова команды сервер возращает сообщение с количеством подключенных клиентов
* Quit – завершает работу с сервером
* MD [Drive:]Path - создание директории
* CD [Drive:]Path - смена текущей директории
* RD [Drive:]Path - удаление директории
* DELTREE [Drive:]Path – удаление директории и всех ее поддиректорий
* MF [[DRIVE:]Path]FileName – создание файла
* DEL [[DRIVE:]Path]FileName – удаление файла 
* LOCK [[DRIVE:]Path]FileName – запрещает удаление файла
* UNLOCK [[DRIVE:]Path]FileName – снимает запрет на удаление с файла
* COPY [drive:]source [drive:]destination - копирует файл или директорию в другую директорию
* MOVE [drive:]source [drive:]destination - перемещает файл или директорию в другую директорию
* PRINT – выводит на экран дерево каталогов

## Компиляция и запуск

Для компиляции проекта введите следующие команды:

```comand line
javac -cp ./src -d bin -encoding UTF-8 ru/gnusinay/server/Server.java
javac -cp ./src -d bin -encoding UTF-8 ru/gnusinay/client/Client.java
```

Для запуска:
1. Необходимо поместить в директорию bin/ru/gnusinay/server файл конфигурации сервера config.properties.
Его можно найти в исходном коде, в каталоге ru/gnusinay/server 

2. Запуск сервера из каталога bin

```comand line
java -cp ./bin ru/gnusinay/server/Server
```

3. Запуск клиента из катаога bin

```comand line
java -cp ./bin ru/gnusinay/client/Client
```

## Настройки сервера (файл config.properties)

SERVER_ADDRESS=127.0.0.1 - адрес сервера

SERVER_PORT=9090         - порт

ROOT=C:                  - имя корневого каталога

TASK_QUEUE_SIZE=20       - длина очереди команд

TASK_WORKER_COUNT=4      - количество потоков выполняющих команды

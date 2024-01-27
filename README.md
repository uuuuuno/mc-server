# Minecraft Server

Этот репозиторий содержит конфигурацию docker-compose для запуска связки серверов Minecraft, включающей прокси, лобби и сервер1.

## Подготовка

Перед запуском серверов убедитесь, что вы обновили `velocity secret` в следующих файлах:

- `./mc-velocity/forwarding.secret` (просто вставьте секрет в пустой файл)
- `./mc-lobby/config/paper-global.yml:100` (secret: 'YOUR-SECRET')
- `./mc-server1/config/paper-global.yml:100` (secret: 'YOUR-SECRET')

### Если вы хотите добавить еще серверы, выполните следующие шаги:

1. Отредактируйте `compose.yaml`, добавив новый контейнер и присвоив ему container_name. Это потребуется во втором шаге.

2. Отредактируйте `./mc-velocity/velocity.toml`, добавив новый сервер в раздел `[servers]`. Пример: `container_name = "container_name:25565"`.

Не забудьте создать папку для нового сервера с файлом `paper-global.yml` и указать в нем `velocity secret`. Также не забудьте отредактировать пути в `compose.yaml` для нового сервера.

## Начало работы

Для запуска серверов вам потребуется установить `docker` и плагин `docker-compose-plugin`.

Чтобы запустить серверы, выполните следующую команду:

```shell
docker compose up -d
```

Это запустит серверы в фоновом режиме.

Обратите внимание, что вначале серверам может потребоваться некоторое время для запуска. Вы можете проверить логи с помощью следующей команды:

```shell
docker compose logs -f
```

Как только серверы будут запущены и работают, вы сможете подключиться к ним, используя `IP-адрес:25565`.
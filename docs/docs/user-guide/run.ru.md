# Запуск

## pboted нужен I2P маршрутизатор

- Установите и запустите I2P маршрутизатор
- Включите SAM API.
- Перезапустите I2P маршрутизатор
- TCP порт 7656 и UDP порт 7655 должны стать доступны

## Рекомендуемый способ запуска pboted, собранного из исходников

- Создайте директорию `/etc/pboted`:

```
sudo mkdir /etc/pboted
```

- Скопируйте образец конфигурационного файла из `contrib/pboted.conf` в `~/.pboted/pboted.conf`:

```
sudo cp contrib/pboted.conf /etc/pboted/pboted.conf
```

- Отредайтируйте конфигурационный файл под Ваши нужды. Образец файла хорошо документирован, комментарии помогут Вам в понимании параметров.
- Создайте пользователя, директории для данных и журналов:

```
sudo useradd pboted -r -s /usr/sbin/nologin
sudo mkdir /var/lib/pboted
sudo chown -R pboted: /var/lib/pboted
sudo mkdir /var/log/pboted
sudo chown -R pboted: /var/log/pboted
```

- Скопируйте образец `systemd` Unit-файла из `contrib/pboted.service` в `/lib/systemd/system/pboted.service`:

```
sudo cp contrib/pboted.service /lib/systemd/system/pboted.service
```

- Перезагрузите конфигурацию `systemd` сервисов и запустите приложение:

```
sudo systemctl daemon-reload
sudo systemctl start pboted.service
```

- Теперь Вы сможете наблюдать работу приложения по записям в журнале. SAM сессия будет отображатся в Web консоли I2P маршрутизатора.

## Запуск в пространстве пользователя

- Скопируйте образец файла конфигурации из `contrib/pboted.conf` в `~/.pboted/pboted.conf`:

```
cp contrib/pboted.conf ~/.pboted/pboted.conf
```

- Отредайтируйте конфигурационный файл под Ваши нужды. Образец файла хорошо документирован, комментарии помогут Вам в понимании параметров.
- Запустите приложение:

```
./pboted
```

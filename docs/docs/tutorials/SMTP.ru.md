# SMTP

_Работа проверена с [Mozilla Thunderbird](https://www.thunderbird.net/en-US/)_

Чтобы иметь возможность отправлять письма по протоколу SMTP Вам нужно:

- Заполнить секцию `[smtp]` в [конфигурационном файле](../user-guide/configuration.md)

```
[smtp]
enabled = true
address = 127.0.0.1
port = 25
```

- Перезапустить **pboted** для применения настроек
- После перезапуска появится возможность подключения по SMTP порту вручную (telnet) или с помощью почтового клиента.

## Как составить письмо

### FROM

Есть два того, как это поле может быть заполнено.

#### 1. Классический

В данном случае поле состоит из трёх частей:

`NAME <IDENTITY_NAME@DOMAIN>`

- NAME - опционально, может содержать имя доступной Bote идентичности.
- IDENTITY_NAME - должно содержать имя доступной Bote идентичности.
- DOMAIN - может содержать любой валидный домен.

Например:

`John Doe <johnd@bote.i2p>`

#### 2. Bote

В этом случае поле содержит две части:

`IDENTITY_NAME <BOTE_ADDRESS>`

- IDENTITY_NAME - должно содержать имя доступной Bote идентичности.
- BOTE_ADDRESS - должно содержать публичную часть Bote идентичности.

Например:

`johnd <24noEIMPvV9CEwrSWQtIsTA7balaZ80ZOGRBAzrsBl5nv9xud~k28d9TQIgXmyyCYtHl8PJASAFDeefSc6EJ81>`

### TO

Очень похоже на поле FROM с одним дополнением к опции 1:   
<IDENTITY_NAME@DOMAIN> должно быть в адресной книге для успешной замены.

Например, если в адресной книге есть запись:

```
johnd1@bote.i2p;John Doe 1;24noEIMPvV9CEwrSWQtIsTA7balaZ80ZOGRBAzrsBl5nv9xud~k28d9TQIgXmyyCYtHl8PJASAFDeefSc6EJ81
```

То Вы можете заполнить FROM так:

`TO: John Doe <johnd1@bote.i2p>`

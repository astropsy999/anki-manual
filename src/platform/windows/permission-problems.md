# Проблеми з дозволом Windows

<!-- toc -->

## Проблеми з дозволом

Якщо ви отримуєте повідомлення "доступ заборонено", деякі файли Anki можуть бути налаштовані на режим лише читання, тобто Anki не може зробити в них запис.

Для вирішення проблеми, можна зробити наступне:

- в області пошуку на панелі запуску введіть cmd.exe і натисніть enter
- у вікні, що відкриється, введіть наступне та натисніть Enter, щоб побачити своє ім’я користувача:

`whoami`

- введіть наступне, натискаючи Enter після кожного рядка та замінюючи ____ (і зберігаючи частину `:F`) своїм іменем користувача яке маєте у результаті попередньої команди

cd %APPDATA%

icacls Anki2 /grant ____:F /t

Ця команда повинна виправити дозволи на папку даних Anki, і тепер зможете запустити програму.

## Антивірус/брандмауер/захист від шкідливих програм

Деякі користувачі стикалися з помилками «відмовлено в дозволі» або «лише для читання», які були спричинені програмним забезпечення безпеки, встановленим на їхній машині. Можливо, вам доведеться додати виняток для Anki або спробувати тимчасово вимкнути програмне забезпечення, щоб виключити його як причину. Деякі користувачі повідомляли, що просте вимкнення програмного забезпечення не вирішило проблему, і довелося або додати виняток для Anki, або видалити програмне забезпечення.

## Проблеми з дозволом налагодження

Якщо після того, як ви виключили антивірус і пов'язані програми, виконали наведені вище кроки і не використовуєте OneDrive, але проблеми не зникають. Виконайте наведені нижче команди в cmd.exe, натискаючи клавішу enter після кожної.

whoami

cd %APPDATA%

icacls Anki2 /t

Тоді, будь ласка, скопіюйте та вставте або зробіть скриншот того, що ви бачите, і опублікуйте це у заявці для служби підтримки.
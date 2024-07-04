# Резервні копії

<!-- toc -->

## Автоматичне резервне копіювання

Anki створить автоматичні резервні копії даних ваших карток. До них входить текст
на картках та інформація про розклад, але не входять звуки чи файли зображень.

Автоматичне резервне копіювання може бути корисним для відновлення після помилок,
але не варто покладатися виключно на нього. Оскільки дані зберігаються на вашому
локальному пристрої, це не захистить вас, якщо ваш пристрій зламається або його вкрадуть.
Радимо поєднати це із [ручним резервним копіюванням](#manual-colpkg-backups).

### Restoring

To restore from an automatic backup:

- Open Anki, and choose Switch Profile from the File menu.
- Click on the "Open Backup" button.
- Select the backup you wish to restore from.

When restoring from a backup, any changes made since the backup was created will be lost.

Anki disables automatic syncing and backups when you restore from a backup. Once you're
happy that you've restored the correct backup, close and re-open Anki to return to normal.

### Anki 2.1.50+

Backups are created periodically. You can configure the time between backups
in the [preferences](preferences.md) screen. The default is 30 minutes.

Certain operations will trigger a backup, even if the configured time has not
elapsed yet:

- A one-way sync download
- Importing a .colpkg file using File>Import
- Tools>Check Database

After backups are two days old, Anki will start removing some of the older ones.
You can control how many daily, weekly and monthly backups you'd like to keep.

Backups created with 2.1.50 will not be importable into older Anki versions.

### Older Anki versions

Each time your collection is closed (when closing Anki, switching
profiles, or doing a full sync download), Anki creates a backup. By default
it will store up to 30 backups; you can adjust this in the [preferences](preferences.md).

## Резервне копіювання colpkg вручну

### Відновлення

Ви можете відновити з резервної копії вручну, використовуючи «Файл»>«Імпорт».

### Створення

У Anki 2.1.50+ ви можете скористатися командою «Файл»>«Створити резервну копію», щоб запустити негайне
резервне копіювання. Це функціонує як звичайне автоматичне резервне копіювання та не включає
мультимедійні файли.

Щоб створити резервну копію яка включає звуки та зображення:

- Виберіть «Експортувати» у меню «Файл».
- Переконайтеся, що вибрано «Пакунок колекції Anki (.colpkg)».
- Увімкніть опцію «включити медіа-файли».

Це створить файл .colpkg, який містить усі ваші картки та будь-які звуки/зображення, які вони використовують.
Радимо зберігати файл у безпечному місці, наприклад на іншому пристрої або в хмарній службі зберігання файлів,
як-от Dropbox або Google Drive.

## AnkiWeb

[Synchronising](./syncing.md) your collection with AnkiWeb provides some level of protection
against your device being lost or stolen. If you need to restore your collection from AnkiWeb,
you can force a one-way sync in the preferences screen, or sync from a new device, and then choose
"Download".

## Deletion log

Anki logs deleted notes to a text file called deleted.txt in your
profile folder. These notes are in a text format that can be read by
File&gt;Import, though please note the import feature only supports a
single note type at one time, so if you have deleted notes from
different note types, you'll need to split the file into separate files
for each note type first.

# Керування файлами та Вашою колекцією

<!-- toc -->

## Перевірка Вашої колекції

Гарною ідеєю буде час від часу перевіряти файл колекції на наявність проблем.
Це можна зробити за допомогою пункту меню Інструменти&gt;Перевірити базу даних.
Перевірка бази даних гарантує, що файл не пошкоджено, перебудовує деякі внутрішні
структури та оптимізує файл.

Коли ви перевіряєте базу даних, ваш список тегів також перебудовується.
Коли ви видаляєте окремі колоди чи карти, Anki не оновлює список використаних тегів,
оскільки це неефективно. Якщо ви хочете очистити зі списку старі теги, які більше не
використовуються, перевірте свою базу даних.

Зверніть увагу, що Anki автоматично оптимізує вашу колекцію кожні 2 тижні.
Ця оптимізація забезпечує хорошу роботу колекції, але вона не перевіряє наявність помилок
і не перебудовує список тегів під час автоматичної оптимізації.

## Розташування файлів

У **Windows** останні версії Anki зберігають ваші файли Anki у папці appdata.
Ви можете отримати доступ до неї, відкривши файловий менеджер і ввівши `%APPDATA%\Anki2`
у полі розташування. Старіші версії Anki зберігали файли Anki в папці під назвою `Anki`
у папці `Documents`.

На комп’ютерах **Mac** останні версії Anki зберігають усі файли в папці
`~/Library/Application Support/Anki2`. Папка Library прихована за замовчуванням,
але її можна відкрити у Finder, утримуючи натиснутою клавішу option під час натискання меню Go.
Якщо ви використовуєте старішу версію Anki, файли Anki будуть у папці `Documents/Anki`.

У **Linux** останні версії Anki зберігають дані в `~/.local/share/Anki2` або
`$XDG_DATA_HOME/Anki2`, якщо ви встановили спеціальний шлях до даних. Старіші версії Anki
зберігали файли в `~/Documents/Anki` або `~/Anki`.

У папці Anki параметри на рівні програми та профілю зберігаються
у файлі під назвою prefs.db.

Також для кожного профілю є окрема папка. Папка містить:

- Ваші нотатки, колоди, карти тощо у файлі під назвою collection.anki2

- Ваші аудіо та зображення в папці collection.media

- Папка резервних копій

- Деякі системні файли

Ви ніколи не повинні копіювати або переміщувати свою колекцію, коли Anki відкрито.
Це може призвести до пошкодження вашої колекції. Також не переміщуйте та не змінюйте
інші файли в папці.

## Параметри запуску

Якщо ви внесли деструктивні зміни на одному комп’ютері та маєте непошкоджену копію
на іншому комп’ютері, ви можете запустити Anki без синхронізації, щоб скористатися
опцією повної синхронізації без попереднього завантаження змін. Подібним чином, якщо
у вас виникли проблеми з Anki, ви можете тимчасово вимкнути додаткові компоненти
(або отримати вказівку про це), щоб перевірити, чи вони спричиняють проблему. Ви можете
зробити обидві ці дії, утримуючи клавішу <kbd>Shift</kbd> під час запуску Anki.

Під час запуску можна вказати власну папку. Це розширена функція, яка в першу чергу
призначена для використання з портативними інсталяціями, і ми рекомендуємо використовувати
розташування за замовчуванням у більшості випадків.

Синтаксис для визначення альтернативної папки такий:

    anki -b /path/to/anki/folder

- Якщо у вас кілька профілів, ви можете передати -p &lt;name&gt; завантажити
  конкретний профіль.
- Якщо ви передасте -p some-fake-name, Anki відобразить екран профілю під час запуску.
  Якщо профіль не надано, завантажується останній використаний профіль.

- Щоб змінити мову інтерфейсу, використовуйте -l &lt;iso 639-1 мова
  код&gt;, наприклад "-l ja" для японської мови.

Якщо ви завжди хочете використовувати власне розташування папки, ви можете змінити
свій ярлик для Anki. У Windows клацніть правою кнопкою миші ярлик, виберіть «Властивості»,
виберіть вкладку «Ярлик» і додайте «-b \\шлях\\до\\папки даних\\» після шляху до програми,
що має виглядати як щось на зразок

    "C:\Program Files\Anki\anki.exe" -b "C:\AnkiDataFolder"

Ви також можете використовувати цю техніку з опцією -l, щоб легко використовувати
Anki різними мовами.

У Windows слід використовувати зворотній слеш (\\), а не слеш (/).

На Mac немає простого способу змінити поведінку під час натискання піктограми Anki,
але можна запустити Anki за допомогою спеціальної базової папки з терміналу:

    open /Applications/Anki.app --args -b ~/myankifolder

Крім того, ви можете визначити змінну середовища "ANKI_BASE".
У Windows ви можете визначити змінну середовища за допомогою:

    set "ANKI_BASE=C:/path/to/AnkiDataFolder"

У Linux і macOS можна використовувати:

    export ANKI_BASE="/path/to/AnkiDataFolder"

## DropBox і синхронізація файлів

Ми не рекомендуємо синхронізувати папку Anki безпосередньо за допомогою сторонньою служби
синхронізації, оскільки це може призвести до пошкодження бази даних, коли файли синхронізуються
під час використання.

Якщо ви просто хочете синхронізувати медіафайли, ви можете підключити зовнішні папки до таких служб,
як DropBox. Перегляньте [DropboxWiki: Синхронізація папок поза Dropbox (archive.org)][dropboxwiki-sync-other]
для отримання додаткової інформації.

[dropboxwiki-sync-other]: http://web.archive.org/web/20180919153730/http://www.dropboxwiki.com/tips-and-tricks/sync-other-folders

Якщо ви бажаєте синхронізувати також свою колекцію, настійно рекомендуємо створити скрипт, який
копіює файли з вашої синхронізованої папки до локальної папки, запускає Anki, а потім копіює файли
назад, коли Anki закрито. Це гарантує, що файли ніколи не синхронізуються, коли вони відкриті.

## Мережеві файлові системи

Ми настійно рекомендуємо, щоб Anki зберігала ваші файли на локальному жорсткому диску, оскільки мережеві
файлові системи можуть призвести до пошкодження бази даних. Якщо мережева файлова система є вашим єдиним
вибором, рекомендується регулярно використовувати Інструменти&gt;Перевірити базу даних для виявлення
пошкоджень.

## Запуск з флешки

У Windows Anki можна встановити на USB / флешку та запускати як портативний додаток.
У наступному прикладі припускається, що ваш USB-накопичувач є диском G.

- Скопіюйте папку \\Program Files\\Anki на флешку, щоб
 мати папку типу G:\\Anki.

- Створіть текстовий файл під назвою G:\\anki.bat із таким текстом:

  g:\anki\anki.exe -b g:\ankidata

Якщо ви не хочете, щоб чорне вікно командного рядка залишалося відкритим,
ви можете натомість скористатися:

    start /b g:\anki\anki.exe -b g:\ankidata

- Подвійне клацання на anki.bat повинно запустити Anki з даними користувача,
  що зберігаються в G:\\ankidata.

Необхідно вказати повний шлях, включно з літерою диска. Якщо замість цього
ви спробуєте використати `\anki\anki.exe`, синхронізація перестане працювати.

Синхронізація медіа з AnkiWeb може не працювати, якщо флешку відформатовано як FAT32.
Відформатуйте диск як NTFS, щоб забезпечити правильну синхронізацію медіа.

## Backups

Please see [this section](./backups.md).

## Inaccessible Harddisk

If Anki can't write to files in the [Anki folder](#file-locations), a message
will be displayed on startup saying that Anki can't write to the
harddisk, and Anki will close. If you're unsure how to fix the
permissions, please contact someone near you who is knowledgeable about
computers and can help you out.

## Permissions of Temp Folder

Anki uses the system's temporary folder to store temporary data. If the
permissions of this folder have been changed from the default settings
by a rogue app or buggy antivirus app, Anki will not function properly.

If you're on a Windows 7 machine, the general steps to fix the problem
are listed below. As this is somewhat complicated, please ask someone
knowledgeable about Windows if you are not sure.

1. Click on the start bar, and type in %temp% (including the percents),
   then hit <kbd>Enter</kbd>.

2. Go up one folder, and locate the temp folder. Right click on it, and
   choose Properties.

3. In the security tab, click on Advanced.

4. Click on the Owner tab. If you're not listed as the owner, click the
   button to take ownership.

5. On the permissions tab, ensure that you have full control. On a
   default W7 install the control will actually be inherited from
   c:\\users\\your-username.

## Corrupt Collections

Anki uses a file format that is robust against program and computer
crashes, but it's still possible for your collection to become corrupt
if the files are modified while Anki is open, stored on a network drive,
or corrupted by a bug.

When you run Tools&gt;Check Database, you will receive a message if Anki
detects the file has been corrupted. **The best way to recover from this
is to restore from the most recent [automatic backup](#backups)**, but
if your backup is too old, then you can attempt to repair the corruption
instead.

On Linux, make sure sqlite3 is installed. On a Mac, it should be
installed already. On Windows, download
<http://www.sqlite.org/sqlite-3_6_23.zip>.

Next, create a backup of your collection.anki2 file, in case something
goes wrong with the steps below.

### Linux/macOS

Open a terminal, change to the folder your collection is located in, and
type:

    sqlite3 collection.anki2 .dump > dump.txt

Open the resulting dump.txt file in a text editor, and look at the final
line. If it reads "rollback;", change it to "commit;"

Then run the following in a terminal:

    cat dump.txt | sqlite3 temp.file

Make sure you use temp.file - do not put collection.anki2 on the right,
or you will blank out the file. When you're done, proceed to the final
step.

### Windows

Copy the `sqlite3.exe` program and your deck to your desktop. Then go to
**Start&gt;Run** and type in `cmd.exe`.

If you're on a recent Windows, the command prompt may not start on your
desktop. If you don't see desktop displayed in the command prompt, type
something like the following, replacing 'administrator' with your login
name.

    cd C:\Users\Administrator\Desktop

Then type:

    sqlite3 collection.anki2 .dump > dump.txt

Open the resulting dump.txt file in a text editor, and look at the final
line. If it reads "rollback;", change it to "commit;"

Then run the following in a terminal:

    type dump.txt | sqlite3 temp.file

Make sure you use temp.file - do not put collection.anki2 on the right,
or you will blank out the file. When you're done, proceed to the final
step.

### Final Step

Check that you didn't get an error message, and that temp.file is not
empty. The procedure optimizes the collection in the process, so it's
normal for the new file to be somewhat smaller than the old one.

When you've confirmed the file is not empty:

- rename the original collection.anki2 file to something else

- rename temp.file to collection.anki2

- move collection.anki2 back into your collection folder, overwriting
  the old version

- start Anki and go to Tools&gt;Check Database to make sure the
  collection has been successfully restored.

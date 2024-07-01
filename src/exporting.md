# Exporting

<!-- toc -->

Exporting allows you to save part of your collection as a text file or
packaged Anki deck. To export, click the File menu and choose 'Export'.

## Text Files

If you choose "Notes in Plain Text", Anki will write the contents of the
notes into a text file. Each field is separated by a tab. If you edit
the resulting file and don't modify the first field, you can later
import that file back into Anki and Anki will update your notes based on
your edits, provided you import back into the same note type.

If you find yourself needing to edit the first field as well, you'll
need to change the format of your note type so that the first field is
an ID number rather than actual text. (You can install
the [Add note id](https://ankiweb.net/shared/info/1672832404)
add-on to make this easier.)

In order for formatting to be preserved when you import text back in,
the text is exported with all the HTML formatting embedded in it.

## Упаковані колоди

«Упакована колода» складається з карток, нотаток, типів нотаток і будь-яких звуків і зображень,
об’єднаних у файл із розширенням .apkg або .colpkg. Ви можете використовувати упаковані колоди
для передачі карт між людьми або для резервного копіювання частин вашої колекції.

Є два різних типи упакованих колод.

### Колекція (.colpkg)

Коли ви експортуєте всі колоди з включеним розкладом, це називається «пакет колекції».
Anki скопіює всю вашу колекцію у файл із розширенням .colpkg і розмістить його на робочому столі.
Пакет колекції використовується для резервного копіювання вашої колекції або її копіювання на
інший пристрій.

Пакети колекцій, створені за допомогою попередніх версій Anki,
називалися collection.apkg.

Коли цей файл буде пізніше імпортовано, Anki видалить усі поточні картки в колекції
та замінить колекцію елементами у файлі. Це корисно для копіювання вашої колекції
між пристроями.

Існуючі медіафайли у вашій колекції не видаляються під час імпорту пакета колекції.
Щоб видалити невикористані носії, скористайтеся інструментом&gt;Перевірити носії.

Якщо ви виберете формат Anki 2.1.50+ Collection Package, імпорт і експорт будуть швидшими,
а мультимедійні файли будуть стиснуті, але отриманий файл .colpkg не зможуть прочитати
старіші клієнти Anki.

### Колода (.apkg)

Упаковані колоди містять одну колоду (і будь-які дочірні колоди, які вона може мати).
У них ім’я файлу закінчується на .apkg, але ім’я файлу відрізняється від collection.apkg.
Коли ви імпортуєте колоду, Anki додасть вміст у вашу колекцію, а не перезапише її.

Якщо деякі нотатки в пакеті колоди були раніше імпортовані, Anki збереже версію з часом останньої зміни.
Отже, якщо ви завантажуєте оновлену колоду, зміни, внесені в оновлену версію, також буде внесено у вашу колекцію,
але якщо ви повторно імпортуєте незмінену колоду після внесення змін у свою колекцію,
зміни у вашій колекції збережуться.

Якщо ви вирішите не включати інформацію про розклад, Anki вважатиме, що ви ділитеся колодою з іншими людьми,
і видалить позначені та вилучені теги, щоб вони мали її чисту копію.

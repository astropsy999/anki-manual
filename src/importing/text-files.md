# Текстові файли

<!-- toc -->

Будь-який **звичайний текстовий** файл, який містить поля, розділені комами, крапками з комою або символами табуляції,
можна імпортувати в Anki за виконання деяких умов.

- Файли мають бути простим текстом (myfile.txt). Інші формати,
  наприклад myfile.xls, myfile.rtf, myfile.doc,
  потрібно спочатку зберегти як звичайний текстовий файл.

- Файли мають бути у форматі UTF-8 (див. нижче).

- Перший рядок визначає роздільний символ – якщо Anki знаходить
  «;» у першому рядку використає це, якщо знайде кому -
  використає її, тощо.

- Anki визначає кількість полів у файлі, дивлячись на перший
  (без коментарів) рядок. Якщо деякі з пізніших записів у файлі містять менше
  полів, Anki розглядатиме відсутні поля як порожні. Якщо деякі з записів містять
  додаткові поля, додатковий вміст не буде імпортовано.

Поля у текстовому файлі можна зіставити з будь-яким полем у нотатках,
включаючи поле тегів. Ви можете вибрати, яке поле в текстовому файлі
відповідає полю в нотатці під час імпорту.

Коли ви імпортуєте текстовий файл, ви можете вибрати, у яку колоду помістити карти.
Майте на увазі, що якщо для одного або кількох шаблонів встановлено параметр
заміни колоди, карти потраплять до цієї колоди, а не до тієї,
яку ви обрали.

Це приклад дійсного файлу з трьома полями:

    яблуко; банан; виноград
    деякий текст; інший текст; ще більше тексту

Існує два способи додати в поля символи нового рядка або роздільника полів.

**Виключіть символи, помістивши вміст поля
в лапки**:

    привіт;"це
    відповідь у два рядки"
    два; це однорядкове поле
    "це включає;(крапка з комою)"; інше поле

Оскільки лапки використовуються для позначення початку та кінця поля,
якщо ви бажаєте включити їх у своє поле, вам потрібно замінити одну
подвійну лапку двома подвійними лапками, щоб «виключити» їх із
звичайної обробки, наприклад:

    поле одне;"поле друге з ""екранованими лапками"" всередині"

Коли ви використовуєте програму для роботи з електронними таблицями, як-от Libreoffice, для створення файлу CSV,
вона автоматично подбає про екранування подвійних лапок.

**Використовуйте нові рядки HTML**:

    привіт; це<br>відповідь у два рядки
    два; це один рядок

Вам потрібно ввімкнути прапорець «Дозволити HTML у полях» у діалоговому вікні імпорту,
щоб нові рядки HTML працювали.

Екранування кількох рядків не працюватимуть належним чином, якщо ви використовуєте закриті
видалення, які охоплюють кілька рядків. У цьому випадку використовуйте натомість
символи нового рядка HTML.

Ви також можете додати теги до іншого поля та вибрати його як поле тегів у
діалоговому вікні імпорту:

    перше поле;друге поле;теги

Це приклад дійсного файлу, де перший рядок ігнорується (\#):

    # це коментар і він ігнорується
    foo bar;bar baz;baz quux
    поле1;поле2;поле3

## Електронні таблиці та UTF-8

Якщо у вашому файлі є нелатинські символи (наприклад, наголоси, японські символи тощо), Anki очікує, що файли будуть
збережені в «кодуванні UTF-8». Найпростіший спосіб зробити це — використовувати безкоштовну програму для роботи з
електронними таблицями LibreOffice замість Excel для редагування файлу, оскільки вона підтримує UTF-8, а також
правильно експортує багаторядковий вміст, на відміну від Excel. Якщо ви хочете й надалі використовувати Excel, перегляньте
[цю публікацію на форумі](https://docs.google.com/document/d/12YE_FS6A9ANLTESJNtPP116ti4nNmCBghyoJBRtno_k/edit?usp=sharing) для отримання додаткової інформації.

Щоб зберегти електронну таблицю у файлі, який Anki може читати за допомогою LibreOffice, перейдіть у меню File&gt;Save as,
а потім виберіть CSV як тип файлу. Після прийняття параметрів за замовчуванням LibreOffice збереже файл,
і ви зможете імпортувати його в Anki.

## HTML

Anki can treat text imported from text files as HTML (the language used
for web pages). This means that text with bold, italics and other
formatting can be exported to a text file and imported again. If you
want to include HTML formatting, you can check the "allow HTML in
fields" checkbox when importing. You may wish to turn this off if you’re
trying to import cards whose content contains angle brackets or other
HTML syntax.

If you wish to use HTML for formatting your file but also wish to
include angle brackets or ampersands, you may use the following replacements:

| Character | Replacement |
| --------- | ----------- |
| &lt;      | `&lt;`      |
| &gt;      | `&gt;`      |
| &amp;     | `&amp;`     |

## Importing Media

If you want to include audio and pictures from a text file import, copy
the files into the [collection.media folder](../files.md). **Do not put
subdirectories in the media folder, or some features will not work.**

After you’ve copied the files, change one of the fields in your text
file as follows.

    <img src="myimage.jpg">

or

    [sound:myaudio.mp3]

Alternatively, you can use the [find and replace](../browsing.md) feature
in the browse screen to update all the fields at once. If each field
contains text like "myaudio", and you wish to make it play a sound,
you’d search for (.\*) and replace it with "\[sound:\\1.mp3\]", with the
'regular expressions' option enabled.

When importing a text file with these references, you must make sure to
enable the "Allow HTML" option.

You might be tempted to do this in a template, like:

    <img src="{{field name}}">

Anki doesn’t support this for two reasons: searching for used media is
expensive, as each card has to be rendered, and such functionality isn’t
obvious to shared deck users. Please use the find & replace technique
instead.

## Bulk Media

Another option for importing large amounts of media at once is to use
the [media import add-on](https://ankiweb.net/shared/info/1531997860).
This add-on will automatically create notes for all files in a folder
you select, with the filenames on the front (minus the file extension,
so if you have a file named apple.jpg, the front would say 'apple') and
the images or audio on the back. If you would like a different
arrangement of media and filenames, you can [change the note type](../browsing.md) of the created cards afterwards.

## Adding Tags

If you want to add 'tag1' and 'tag2' to every line you’re importing, add
the following to the top of the text file:

    tags:tag1 tag2

## Duplicates and Updating

When importing text files, Anki uses the first field to determine if a
note is unique. By default, if the file you are importing has a first
field that matches one of the existing notes in your collection and that
existing note is the same type as the type you’re importing, the
existing note’s other fields will be updated based on content of the
imported file. A drop-down box in the import screen allows you to change
this behaviour, to either ignore duplicates completely, or import them
as new notes instead of updating existing ones.

The 'match scope' setting controls how duplicates are identified. When
'notetype' is selected, Anki will identify a duplicate if another note
with the same notetype has the same first field. When set to 'notetype and deck',
a duplicate will only be flagged if the existing note also happens to be
in the deck you are importing into.

If you have updating turned on and older versions of the notes you’re
importing are already in your collection, they will be updated in place
(in their current decks) rather than being moved to the deck you have
set in the import dialog. If notes are updated in place, the existing
scheduling information on all their cards will be preserved.

For info on how duplicates are handled in .apkg files, please see the
[Deck Packages](../exporting.md#packaged-decks) section.

## File Headers

Anki 2.1.54+ supports certain headers that can be included in the text file to
make importing more powerful or convenient. They consist of `#key:value` pairs
and must be listed in separate lines at the top of the file, though the [tags line](#adding-tags)
may precede them. Since header lines start with the comment character `#`, earlier
Anki clients will just ignore them.

You must enable the new importing option in the preferences screen to use this on
2.1.54. On 2.1.55, the new importing path is the default.

| Key               | Allowed Values                                                                             | Behaviour                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| `separator`       | `Comma`, `Semicolon`, `Tab`, `Space`, `Pipe`, `Colon`, or the according literal characters | Determines the field separator.                                                                                 |
| `html`            | `true`, `false`                                                                            | Determines whether the file is treated as HTML.                                                                 |
| `tags`            | List of tags, separated by spaces                                                          | Same as [the old syntax](#adding-tags).                                                                         |
| `columns`         | List of names, separated by the previously set separator                                   | Determines the number of columns and shows their given names when importing.                                    |
| `notetype`        | Notetype name or id                                                                        | Presets the notetype, if it exists.                                                                             |
| `deck`            | Deck name or id                                                                            | Presets the deck, if it exists.                                                                                 |
| `notetype column` | `1`, `2`, `3`, ...                                                                         | Determines which column contains the notetype name or id of each note, see [Notetype Column](#notetype-column). |
| `deck column`     | `1`, `2`, `3`, ...                                                                         | Determines which column contains the deck name or id of each note, see [Deck Column](#deck-column).             |
| `tags column`     | `1`, `2`, `3`, ...                                                                         | Determines which column contains the tags of each note.                                                         |
| `guid column`     | `1`, `2`, `3`, ...                                                                         | Determines which column contains the GUID of each note, see [GUID Column](#guid-column).                        |

Some headers have further implications.

### Notetype Column

Usually, all notes from a file will be mapped to a single notetype, and you may
choose which column should be mapped to which field of that notetype.

That changes, if there is a column with notetype names or ids. This allows to
import notes with different notetypes, and their fields will be mapped implicitly:
The first regular column is used for the first field of any note regardless of
its notetype, the second regular column for the second field, and so on.
A 'regular column' here being a column that does not contain special information
like decks, tags, notetypes or GUIDs.

### Deck Column

Usually, any new cards created as a result of importing a text file will be placed
in a single deck of your choice. If the file contains a deck column, however, new
cards of a note will be placed in its specified deck instead. If the deck does not
exist, a deck with the given name will be created.

### GUID Column

GUID stands for _Globally Unique Identifier_. When you create notes in Anki, Anki
assigns each note a unique ID, which can be used for duplicate checking. If you
export your notes with the GUID included, you can make changes to the notes, and
as long as you do not modify the GUID field, you'll be able to import the notes back
in to update the existing notes.

Please note that the GUID is intended to be created by Anki. If you are creating
your own IDs, such as MYNOTE0001, then it's recommended that you place the IDs
in the first field, instead of assigning them to Anki's internal GUID. When importing,
Anki is able to use either the first field or the GUID for duplicate checking, so you do not
need to make IDs a GUID in order to be able to update your notes.

One other thing to note is that the 'duplicate' option will not work for rows that have a
non-empty GUID. If a GUID is provided, and already exists in the collection, a duplicate will
not be created.

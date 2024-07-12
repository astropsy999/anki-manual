# Генерація карток

<!-- toc -->

## Зворотня карта

Ви можете переглянути [відео про реверсування карток](http://www.youtube.com/watch?v=DnbKwHEQ1mA&yt:cc=on) на YouTube.

Якщо ви хочете створити картки, які йдуть в обох напрямках (наприклад, обидва
«ookii»→«big» і «big»→«ookii»), у вас є кілька варіантів. Найпростішим є вибір типу вбудованої нотатки «Основна (і перевернута картка)». Це створить дві картки, по одній у кожному напрямку.

Якщо ви хочете створити зворотні картки лише для деяких матеріалів (можливо, ви хочете витратити час лише на вивчення реверсів для найважливішого матеріалу, або деякі з ваших карток не має сенсу перевертати), ви можете вибрати «Основний (додаткова перевернута картка)” тип нотатки. Цей тип генерує лише передню картку, коли ви заповнюєте перші два поля; якщо ви додатково введете щось у полі «Додати реверс» (наприклад, «y»), Anki також згенерує зворотню картку. Вміст цього поля ніколи не відображатиметься на картці.

## Створення та видалення карток

Anki не створюватиме картки з порожніми лицьовими сторонами. Таким чином, якщо «Моє поле» буде порожнім, а шаблон першої картки міститиме лише це поле, картку не буде створено.

Коли ви редагуєте раніше додану нотатку, Anki автоматично створить додаткові картки, якщо вони раніше були порожніми, але тепер такими не є. Однак якщо ваші зміни зробили деякі картки порожніми, але раніше вони не були, Anki не видалить їх негайно, оскільки це може призвести до випадкової втрати даних. Щоб видалити порожні картки, перейдіть до Інструменти → Очистити картки у головному вікні. Вам буде показано список порожніх карток і ви зможете видалити їх.

Через те, як працює генерація карток, неможливо вручну видалити окремі картки, оскільки вони просто відтворяться під час наступного редагування нотатки. Натомість ви повинні зробити відповідні поля умовно порожніми, а потім використати параметр Порожні Картки.

Anki не враховує спеціальні поля чи текст, що не є полем, для створення карток. Таким чином, якщо ваш передній шаблон виглядатиме так, картка не буде створена, якщо "Країна" буде порожньою:

    Де знаходиться {{Країна}} на мапі?

## Вибіркова генерація карток

Іноді вам може знадобитися створити додаткові картки лише для деяких матеріалів, наприклад, щоб перевірити здатність пригадувати найважливіші слова з набору. Ви можете досягти цього, додавши додаткове поле до своєї нотатки та додавши в нього певний текст (наприклад, «1») у нотатках, для яких ви хочете мати додаткову картку. Потім у шаблоні картки ви можете зробити створення картки залежним від того, що це поле не є порожнім. Для отримання додаткової інформації про це дивіться розділ умовної заміни нижче.

## Умовне заміщення

Певний текст, поля чи HTML-код можна додати до своїх карток, лише якщо поле порожнє або не порожнє. Приклад:

    Цей текст завжди відображається.

    {{#FieldName}}
        Цей текст відображається, лише якщо FieldName містить текст
    {{/FieldName}}

    {{^FieldName}}
        Цей текст відображається, лише якщо поле FieldName порожнє
    {{/FieldName}}

Реальний приклад показує тег, лише якщо поле не пусте:

    {{#Tags}}
        Теги: {{Tags}}
    {{/Tags}}

Або скажімо, що ви хочете відобразити певне поле синім кольором на лицьовій стороні вашої картки, якщо на зворотному боці є додаткові примітки (можливо, факт наявності приміток служить нагадуванням про те, що вам слід витратити більше часу на обдумування відповіді). Ви можете оформити поле таким чином:

    {{#Notes}}
        <span style="color:blue;">
    {{/Notes}}

    {{FieldToFormat}}

    {{#Notes}}
        </span>
    {{/Notes}}

Ви також можете використовувати умовне заміщення, щоб контролювати, які саме картки генеруються. Це працює, оскільки Anki не буде генерувати картки з порожньою передньою стороною. Наприклад, розглянемо картку з двома полями на лицьовій стороні:

    {{Expression}}
    {{Notes}}

Зазвичай картку буде створено, якщо поле Expression або Notes містить текст. Якщо ви хочете, щоб картка згенерувалася, якщо Expression не є порожнім, можете змінити шаблон на такий:

    {{#Expression}}
        {{Expression}}
        {{Notes}}
    {{/Expression}}

І якщо бажаєте обидва поля, ви можете використати дві умовні заміни:

    {{#Expression}}
        {{#Notes}}
            {{Expression}}
            {{Notes}}
        {{/Notes}}
    {{/Expression}}

Майте на увазі, що це працює лише тоді, коли ви розміщуєте код умовної заміни на _передній_ стороні картки; якщо зробите це на звороті, ви просто отримаєте картки з порожньою зворотною стороною. Подібним чином, оскільки перевіряється, чи переднє поле є порожнім, важливо переконатися, що ви загорнули «всю» лицьову сторону в
умовний вираз; наприклад, наступне не працюватиме належним чином:

    {{#Expression}}
        {{Expression}}
    {{/Expression}}
    {{Notes}}

## Порожні зворотні сторони

Для створення картки розглядається лише лицьова сторона картки. Наприклад, якщо у вас є передній шаблон:

    {{Field 1}}

та зворотний шаблон:

    {{Field 2}}

Тоді картку буде згенеровано, якщо Field 1 не порожнє. Якщо Field 2 порожнє, картку все одно буде згенеровано, і ви отримаєте порожню зворотну сторону.

Якщо хочете уникнути порожньої зворотної сторони, вам потрібно буде розмістити обов’язкове поле на передньому шаблоні як умовне, наприклад:

    {{#Field 2}}
        {{Field 1}}
    {{/Field 2}}

Це забезпечить створення картки, лише якщо Field 2 і Field 1 непорожні.

## Limitations in Older Anki Versions

The following limitations do not apply to Anki 2.1.28+ and AnkiMobile 2.0.64+.

Older Anki versions cannot use negated conditionals for card generation.
For example, on Anki 2.1.28, the following would add a card if a field
called AddIfEmpty is empty, and Front is non-empty:

    {{^AddIfEmpty}}
        {{Front}}
    {{/AddIfEmpty}}

On earlier Anki versions, the negated conditional is ignored, and card
generation will depend only on Front being non-empty.

Mixing **AND** and **OR** conditions can also cause problems on older versions.
For example, the following ("add the card if A **OR** B **OR** C is non-empty")
is fine:

    {{A}}
    {{B}}
    {{C}}

And the following ("add the card if A **AND** B **AND** C are non-empty") is fine:

    {{#A}}
        {{#B}}
            {{#C}}
                {{A}}
            {{/C}}
        {{/B}}
    {{/A}}

But the following ("add the card if A **OR** (B **AND** C) are non-empty") will not work properly:

    {{A}}
    {{#B}}
        {{#C}}
            {{B}}
        {{/C}}
    {{/B}}

## Adding Empty Notes

When you add a new note in Anki 2.1.28+ and AnkiMobile 2.0.64+, if the card
templates and note fields combine to produce no cards, a blank card will be
created using the first template. This allows you to add material even if it's
incomplete, and modify it or the template later to make it valid. If you don't
wish to keep an empty note, you can remove it with the Empty Cards function.

On older Anki versions, Anki refuses to add or import a note if no cards
would be generated.

## Cloze Templates

Please see the [cloze deletion](../editing.md#cloze-deletion) section for background info.

The cloze note type functions differently from regular note types.
Instead of a customizable number of card types, it has a single type
which is shared by all cloze deletions on a note.

As mentioned in the card generation section above, generation of regular
cards depends on one or more fields on the question being non-empty.
Cloze deletion note types are generated differently:

- Anki looks on the front template for one or more cloze replacements,
  like {{cloze:FieldName}}.

- It then looks in the FieldName field for all cloze references, like
  {{c1::text}}.

- For each separate number, a card will be generated.

Because card generation functions differently for cloze deletion cards,
{{cloze:…​}} tags can not be used with a regular note type - they
will only function properly when used with a cloze note type.

Conditional generation provides a special field so you can check which
card you are rendering. If you wanted to display the "hint1" field on
the first cloze, and "hint2" field on the second cloze for example, you
could use the following template:

    {{cloze:Text}}

    {{#c1}}
        {{Hint1}}
    {{/c1}}

    {{#c2}}
        {{Hint2}}
    {{/c2}}

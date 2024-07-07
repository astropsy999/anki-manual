# Стилізація та HTML

<!-- toc -->

## Стилізація карток

Ви можете переглянути [відео про оформлення карток](http://www.youtube.com/watch?v=F1j1Zx0mXME&yt:cc=on)
на YouTube. На відео показано інтерфейс Anki 2.0, але концепції в основному ті самі.

До розділу стилів на екрані карток можна отримати доступ, натиснувши кнопку «Стилі» поруч із кнопкою
«Назад до шаблону». У цьому розділі ви можете змінити колір фону картки, шрифт за замовчуванням,
вирівнювання тексту тощо.

Доступні стандартні варіанти:

**font-family**\
Назва шрифту для використання на картці. Якщо у вашому шрифті є пробіли, як-от «MS Unicode»,
то вам потрібно взяти назву шрифту в подвійні лапки, як у цьому реченні. Також можна використовувати
декілька шрифтів на одній картці; інформацію про це дивіться нижче.

**font-size**\
Розмір шрифту в пікселях. Змінюючи його, переконайтеся,
що ви залишили px у кінці.

**text-align**\
Чи слід вирівнювати текст по центру, ліворуч чи праворуч.

**color**\
Колір тексту. Прості назви кольорів, як-от blue, lightyellow, тощо, підійдуть,
або ви можете використовувати коди кольорів HTML для вибору довільних кольорів. Перегляньте
[цю веб-сторінку](https://htmlcolorcodes.com/) для отримання додаткової інформації.

**background-color**\
Колір фону картки.

Будь-який CSS можна розмістити в розділі стилів – досвідчені користувачі можуть забажати,
наприклад, додати фонове зображення або градієнт. Якщо вам цікаво, як отримати певне форматування,
знайдіть в Інтернеті інформацію про те, як це зробити в CSS, оскільки доступна велика кількість
документації.

Стиль спільний для всіх карток, що означає, що коли ви робите коригування, це вплине на всі картки
для цього типу нотаток. Однак також можна вказати стиль для кожної картки. У наступному прикладі буде
використано жовтий фон на всіх картках, крім першої:

```css
.card {
  background-color: yellow;
}
.card1 {
  background-color: blue;
}
```

## Зміна розміру зображення

Anki за замовчуванням зменшує зображення відповідно до розміру екрана. Ви можете змінити це,
додавши наступне до нижньої частини розділу стилів (за межами стандартного
`.card { ... }`):

```css
img {
  max-width: none;
  max-height: none;
}
```

У AnkiDroid іноді виникають [проблеми з масштабуванням зображень відповідно до розміру екрана](https://github.com/ankidroid/Anki-Android/issues/3612). Встановлення максимальних розмірів зображення за допомогою css повинно виправити це,
але, здається, воно ігнорується з AnkiDroid 2.9. Виправлення полягає в додаванні `!important` до кожної директиви стилю, наприклад:

```css
img {
  max-width: 300px !important;
  max-height: 300px !important;
}
```

Якщо ви спробуєте змінити стиль для зображень і виявите, що зірочка, яка з’являється на позначених картках,
змінюється (наприклад, вона стає занадто великою), ви можете налаштувати її за допомогою наступного:

```css
img#star {
  ...;
}
```

Ви можете досліджувати стиль карток в інтерактивному режимі за допомогою Chrome:

<https://addon-docs.ankiweb.net/porting2.0.html#webview-changes>

Anki 2.1.50+ підтримує зміну розміру зображення в редакторі.

## Стилізація полів

Стиль за замовчуванням застосовується до всієї картки. Ви також можете зробити певні поля чи частину
картки іншим шрифтом, кольором тощо. Це особливо важливо під час вивчення іноземних мов, оскільки
Anki іноді не зможе правильно відобразити символи, якщо не вибрано відповідний шрифт.

Скажімо, у вас є поле «Вираз» і ви хочете надати йому тайський шрифт OSX «Ayuthaya». Уявіть, що ваш шаблон:

    What is {{Expression}}?

    {{Notes}}

Що нам потрібно зробити, це обернути текст, який потрібно стилізувати, у HTML. Перед текстом ми поставимо наступне:

    <div class=mystyle1>

А за цим:

    </div>

За допомогою обтікання тексту, як описано вище, ми наказуємо Anki стилізувати обернутий текст за допомогою спеціального стилю під назвою «mystyle1», який ми створимо пізніше.

Таким чином, якщо потрібно повністю стилізувати `«What is …​?» Expression` для використання тайського шрифту, потрібно скористатися:

    <div class=mystyle1>What is {{Expression}}?</div>

    {{Notes}}

А якщо потрібно, щоб лише саме поле виразу використовувало тайський шрифт:

    What is <div class=mystyle1>{{Expression}}</div>?

    {{Notes}}

Після редагування шаблону нам потрібно перейти до розділу «Стилі» в шаблоні. Перед редагуванням, він повинен виглядати приблизно так:

```css
.card {
  font-family: arial;
  font-size: 20px;
  text-align: center;
  color: black;
  background-color: white;
}
```

Додайте свій новий стиль нижче, щоб він виглядав так:

```css
.card {
  font-family: arial;
  font-size: 20px;
  text-align: center;
  color: black;
  background-color: white;
}

.mystyle1 {
  font-family: ayuthaya;
}
```

Ви можете включити в `mystyle1` будь-яку стилізацію. Якщо хочете збільшити розмір шрифту, ви повинні змінити `mystyle1` таким чином:

```css
.mystyle1 {
  font-family: ayuthaya;
  font-size: 30px;
}
```

До вашої колоди також можна додати власні шрифти, тож вам не потрібно встановлювати їх на комп’ютері чи мобільному пристрої. Для отримання додаткової інформації перегляньте розділ [встановлення шрифтів](#installing-fonts).

## Кнопки відтворення звуку

Якщо аудіо або текст включено у мовлення на ваші картки, Anki покаже кнопки, на які можна натиснути, щоб відтворити аудіо.

Якщо ви не бажаєте бачити кнопки, ви можете сховати їх
на екрані налаштувань.

Ви можете налаштувати їх зовнішній вигляд у стилі вашої картки, наприклад
щоб зробити їх меншими та кольоровими, ви можете використати наступне:

```css
.replay-button svg {
  width: 20px;
  height: 20px;
}
.replay-button svg circle {
  fill: blue;
}
.replay-button svg path {
  stroke: white;
  fill: green;
}
```

## Напрямок тексту

Якщо ви використовуєте мову, яка пишеться справа наліво, наприклад арабську чи іврит,
ви можете додати властивість CSS `direction` до розділу .card для правильного відображення під час перегляду:

```css
.card {
  direction: rtl;
}
```

Це змінить напрямок усієї картки. Ви можете змінити напрямок
лише певних полів, загорнувши їх посилання в деякий HTML:

    <div dir="rtl">{{Front}}</div>

Щоб змінити напрямок полів у редакторі, див.
розділ [редагування](../editing.md#customizing-fields).

## Інший HTML

Ваші шаблони можуть містити довільний HTML, що означає, що всі можливості компонування, які використовуються на веб-сторінках Інтернету, також можна використовувати на
картках. Підтримуються такі речі, як таблиці, списки, зображення, посилання на зовнішні сторінки тощо. Наприклад, за допомогою таблиць ви можете змінити макет таким чином, щоб передня і зворотна сторони картки відображалися ліворуч і праворуч, а не зверху і знизу.

Розгляд усіх функцій HTML виходить за рамки цього посібника, але
є багато хороших вступних посібників з HTML, доступних в
Інтернет, якщо захочете дізнатися більше.

## Зовнішній вигляд браузера

Якщо ваші шаблони карток складні, вам може бути важко прочитати стовпці запитань і відповідей (так звані «Передня» та «Задня») у [списку карток](../browsing.md#cardnote-table). Параметр «вигляд у веб-браузері» дозволяє визначити спеціальний шаблон, який буде використовуватися лише у веб-браузері, тож ви можете включити лише важливі поля та змінити порядок, якщо хочете. Синтаксис такий же, як і в стандартних шаблонах карток.

## Спеціальний CSS для платформи

Anki визначає деякі спеціальні класи CSS, які дозволяють визначати різні стилі для різних платформ. У наведеному нижче прикладі показано, як змінити шрифт залежно від того, де ви переглядаєте:

```css
/* Windows */
.win .example {
  font-family: "Example1";
}
/* macOS */
.mac .example {
  font-family: "Example2";
}
/* Linux desktops */
.linux:not(.android) .example {
  font-family: "Example3";
}
/* both Linux desktops, and Android devices */
.linux .example {
  font-family: "Example4";
}
/* both Android and iOS */
.mobile .example {
  font-family: "Example5";
}
/* iOS */
.iphone .example,
.ipad .example {
  font-family: "Example6";
}
/* Android */
.android .example {
  font-family: "Example7";
}
```

Та в шаблоні:

```html
<div class="example">{{Field}}</div>
```

Для вибору також можна використовувати такі властивості, як .gecko, .opera та .ie
певні браузери під час використання AnkiWeb. Будь ласка, подивіться
<http://rafael.adm.br/css_browser_selector/> з повним списком параметрів.

## Installing Fonts

If you’re using Anki on a work or school computer where you don’t have
permission to install new fonts, or you’re using Anki on a mobile
device, it’s possible to add fonts directly to Anki.

To add a font to Anki, it must be in the TrueType format. TrueType fonts
have a filename ending in .ttf, such as "Arial.ttf". Once you’ve located
a TrueType font, we’ll need to add it to the media folder:

1. Rename the file, adding an underscore at the start, so it becomes
   like "\_arial.ttf". Adding an underscore will tell Anki that this
   file will be used on a template, and should not be deleted when
   checking for unused media.

2. In your computer’s file browser, go to your [Anki Folder](../files.md),
   and then a folder called "User 1" (or your profile name if you’ve
   renamed/added profiles).

3. Inside the folder, you should see a folder called collection.media.
   Drag the renamed file to that folder.

After that, we need to update the template:

1. Click **Add** at the top of the main screen, and then select the
   note type you want to change with the top left button.

2. Click **Cards**.

3. In the styling section, add the following text to the bottom (after
   the last "}" character), replacing "\_arial.ttf" with the name of
   the file you copied into your media folder:

```css
@font-face {
  font-family: myfont;
  src: url("_arial.ttf");
}
```

Only change the "arial" part, not the "myfont" part.

After that, you can either change the font for the entire card, or for
individual fields. To change the font for the entire card, simply locate
the font-family: line in the .card section and change the font to
"myfont". To change the font for only certain fields, please see the
[Field Styling](#field-styling) instructions above.

Please make sure the filenames match exactly. If the file is called
arial.TTF and you write arial.ttf in your card templates, it will not
work.

## Night Mode

You can customize the way templates appear when night mode is enabled in
the preferences screen.

If you wanted a lighter grey background, you could use
something like:

```css
.card.nightMode {
  background-color: #555;
}
```

If you have a 'myclass' style, the following would show the text in
yellow when night mode is enabled:

```css
.nightMode .myclass {
  color: yellow;
}
```

## Fading and Scrolling

Anki will automatically scroll to the answer by default. It looks for an
HTML element with id=answer, and scrolls to that. You can place the id
on a different element to adjust the scrolling position, or remove the
id=answer to turn off scrolling.

The question side of a card fades in by default. If you wish to adjust
this delay, you can place the following at the top of your front card
template:

```html
<script>
  qFade = 100;
  if (typeof anki !== "undefined") anki.qFade = qFade;
</script>
```

100 (milliseconds) is the default; set to 0 to disable fading.

## Javascript

As Anki cards are treated like webpages, it is possible to embed some
Javascript on your cards via the card template. For a good reference
please read [this post](https://forums.ankiweb.net/t/card-templates-user-input-101-buttons-keyboard-shortcuts-etc-guide/13756)
in the forums.

Because Javascript is an advanced feature and so many things can go
wrong, **Javascript functionality is provided without any support or
warranty**. We can not provide any assistance with writing Javascript,
and can not guarantee any code you have written will continue to work
without modification in future Anki updates. If you are not comfortable
addressing any issues you encounter on your own, then please avoid using
Javascript.

Each Anki client may implement card display differently, so you will
need to test the behaviour across platforms. A number of clients are
implemented by keeping a long running webpage and dynamically updating
parts of it as cards are reviewed, so your Javascript will need to
update sections of the document using things like
document.getElementById() rather than doing things like
document.write().

Functions like window.alert may not be available. Anki will write
javascript errors to the terminal, so you'll need to [view the console](https://addon-docs.ankiweb.net/console-output.html#console-output) to
see them. To debug issues with JavaScript, you can use Chrome's
[inspector](https://addon-docs.ankiweb.net/debugging.html#webviews).

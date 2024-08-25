# Налаштування колоди

<!-- toc -->

Налаштування колоди в основному контролюють, як Anki планує картки. Рекомендується
використовувати стандартні налаштування протягом кількох тижнів, щоб ознайомитися з роботою Anki, перш ніж почати змінювати параметри. Будь ласка, переконайтеся, що ви розумієте ці налаштування, перш ніж змінювати їх, оскільки помилки можуть знизити ефективність Anki.

Доступ до налаштувань колоди можна отримати, виконавши такі дії:

- Натиснувши на значок шестерні на екрані `Колоди`.
- Вибравши колоду на екрані `Колоди`, а потім натиснувши `Параметри` внизу екрана.
- Натиснувши на `Більше` > `Налаштування` під час режиму перегляду.
- Натиснувши клавішу `о` під час режиму перегляду.

Ця сторінка описує параметри, які показуються в Anki 2.1.45+ при включеному планувальнику v2 або v3. У старіших версіях деякі параметри можуть бути недоступні або знаходитись в іншому розділі. Будь ласка, зверніть увагу, що планувальник v1 більше не підтримується в Anki 2.1.50+. Якщо ви ще не оновилися до v2 або v3, вам буде запропоновано оновитися при спробі перегляду карток у версії 2.1.50+.

Для отримання додаткової інформації про налаштування колоди, будь ласка, зверніться до:

- [Пояснення Налаштувань Колоди](https://forums.ankiweb.net/t/deck-options-explained/213)
- [Налаштування Колоди на Ментальній Мапі](https://forums.ankiweb.net/t/deck-options-in-a-mental-map/15757)

## Пресети

Anki дозволяє ділитися налаштуваннями між різними колодами, що полегшує
оновлення параметрів у багатьох колодах одночасно. Для цього налаштування
групуються в _пресети_. Усталено усі новостворені колоди використовують
один і той самий пресет.

Якщо ви хочете змінити налаштування лише однієї колоди, натисніть на
значок стрілки у верхньому правому куті вікна налаштувань колоди. Доступні такі опції:

- **Зберегти**: Зберігає всі зміни, внесені з моменту відкриття екрану налаштувань колоди.
- **Додати**: Додає новий пресет із типовими налаштуваннями.
- **Клонувати**: Клонує поточний пресет, що корисно, якщо ви
  хочете змінити певні параметри, зберігаючи решту без змін.
- **Перейменувати**: Змінює назву поточного пресету.
- **Видалити**: Видаляє поточний пресет. Це вимагатиме односторонності наступної синхронізації.
- **Зберегти для всіх дочірніх колод**: Як _Зберегти_, але також призначає вибраний пресет для всіх
  дочірніх колод обраної.
- **Оптимізувати всі пресети**: Коли FSRS увімкнено, це дозволяє оптимізувати параметри всіх пресетів одночасно.

Налаштування колоди не мають зворотної дії. Наприклад, якщо ви зміните параметр, що контролює затримку після помилки у картці, картки, на яких ви помилилися до зміни параметра, залишатимуться з попередньою затримкою, а не новою.

## Дочірні колоди

Якщо у вашій колоді є дочірні, кожній з них можна призначити окремий пресет. Коли Anki показує картку, вона перевіряє, в якій дочірній колоді знаходиться картка, і використовує налаштування для цієї колоди. Однак є деякі винятки:

- Ліміти нових карток/день і повторень/день [поводяться](#daily-limits) по-різному залежно від обраної версії планувальника.
- Опції [порядку відображення](#display-order) у планувальнику v3 беруться з колоди, вибраної для вивчення, а не з колоди поточної картки.

Наприклад, припустимо, що у вас є така структура:

    - Колода A (Пресет 1)
      - Колода A::Дочірня колода B (Пресет 2)
        - Картка B1
        - Картка B2

Пресети 1 та 2 ідентичні, за винятком двох пунктів:

- Пресет 1:
  - Нові картки - Етапи навчання: 1хв 10хв
  - Порядок відображення - Пріоритет нових/повторень: Змішати з повтореннями
- Пресет 2:
  - Нові картки - Етапи навчання: 20хв 2год
  - Порядок відображення - Пріоритет нових/повторень: Показати після повторень

Якщо ви вибираєте для вивчення Колоду A:

- Етапи навчання для всіх нових карток будуть 1хв 10хв (застосовується пресет 1)
- Усі нові картки будуть змішані з повтореннями (застосовується пресет 1)

Якщо ви вибираєте для вивчення Дочірню колоду B:

- Етапи навчання для всіх нових карток будуть 20хв 2год (застосовується пресет 2)
- Усі нові картки будуть показані після повторень (застосовується пресет 2)

## Щоденні ліміти

### Нові Картки/День

Цей параметр контролює, скільки нових карток додається кожного дня, коли ви користуєтесь програмою. Якщо вивчаєте менше, ніж ліміт, або пропускаєте день, наступного дня кількість нових карток повернеться до встановленого ліміту — вони не накопичуються.

Коли колоди вкладені (наприклад, Батьківська, Батьківська::Дочірня, Батьківська::Дочірня::Онука), спосіб застосування лімітів залежить від версії планувальника.

- v1 застосовує ліміти батьківської колоди до дочірніх, незалежно від того, на яку колоду ви натиснули.
- v2 діє подібно до v1 для нових карток. Для повторень враховуються лише ліміти колоди, на яку ви натиснули.
- v3 враховує ліміти колоди, на яку ви натиснули, і будь-яких колод всередині неї. Ліміти батьківських колод вище тієї, яку ви вибрали, ігноруються.

Для отримання додаткової інформації перегляньте сторінку [планувальника v3](https://faqs.ankiweb.net/the-2021-scheduler.html#daily-limits).

Вивчення нових карток тимчасово збільшує кількість щоденних повторень, оскільки вивчений матеріал потрібно повторювати кілька разів, перш ніж інтервали між повтореннями значно збільшаться. Якщо ви постійно вивчаєте 20 нових карток на день, очікуйте, що кількість щоденних повторень буде приблизно 200 карток/день. Ви можете зменшити кількість необхідних повторень, вводячи менше нових карток щодня або вимикаючи показ нових карток, поки не зменшиться навантаження на повторення. Деякі користувачі Anki з ентузіазмом вивчають сотні нових карток у перші дні, а потім відчувають перевантаження через велику кількість необхідних повторень.

### Максимальна кількість повторень на день

Цей параметр дозволяє встановити верхнє обмеження кількості щоденних повторень. Коли це обмеження досягнуто, Anki не буде показувати більше карток цього дня, навіть якщо деякі з них залишаються в черзі. Якщо вивчаєте картки послідовно, це налаштування може допомогти згладити випадкові піки в кількості карток і вберегти від стресу після тижневої перерви. Коли картки приховані через це налаштування, на екрані з повідомленням про завершення з’явиться пропозиція збільшити обмеження, якщо у вас є на це час.

У [планувальнику v3](https://faqs.ankiweb.net/the-2021-scheduler.html#daily-limits) і планувальнику v1 кількість повторень залежить від батьківських або обраних колод так само, як і для нових карток.

У планувальнику v2 обмеження враховується лише для тієї колоди, яку ви вибрали — будь-які обмеження батьківських або дочірніх колод ігноруються.

Планувальник v3 включає в кількість повторень картки для навчання з затримкою 1+ день, тому ці картки також підпадають під щоденне обмеження.

### Нові картки ігнорують ліміт

Зверніть увагу, що якщо ви використовуєте [планувальник v3](https://faqs.ankiweb.net/the-2021-scheduler.html#daily-limits),типово кількість показу нових карток обмежується кількістю повторень. Якщо ліміт встановлено на 200, і у вас є 190 карток для повторення, максимальна кількість нових карток, які будуть додані, становитиме 10. Якщо ліміт повторень досягнуто, нові картки не будуть показані. Якщо накопичилися повторення, але ви все одно хочете додати нові картки, можете зробити це, призупинивши повторення або збільшивши ліміт повторень. Однак рекомендується утриматися від додавання нових карток, поки не наздоженете, оскільки додавання нових карток під час відставання, лише погіршить ситуацію.

Починаючи з Anki 2.1.61, ця функція є опціональною і може бути вимкнена глобально в налаштуваннях колоди.

### Щоденні обмеження для колоди

Починаючи з версії 2.1.55, стало можливим використовувати єдиний пресет для різних колод разом із дочірніми, із налаштуванням обмежень для кожної з них окремо. Це усуває необхідність створювати клоновані пресети та полегшує налаштування індивідуальних обмежень для дочірніх колод коли є велике вкладення.

Опції:

- Пресет: Обмеження спільне для всіх колод, які використовують цей пресет.
- Ця колода: Обмеження специфічне для цієї колоди.
- Тільки сьогодні: Тимчасова зміна обмеження для цієї колоди на поточний день.

## Нові Картки

Налаштування в цьому розділі впливають лише на нові картки та ті, що знаходяться на початковому [етапі вивчення](studying.md#learningrelearning-cards). Коли картка проходить етап навчання (тобто для неї більше немає кроків у режимі вивчення), вона стає [карткою для повторення](studying.md#review-cards), і налаштування в цьому розділі більше не застосовуються.

### Етапи Вивчення

Цей параметр контролює кількість повторень під час вивчення та затримку між ними. Потрібно ввести одне або більше значень затримки, розділених пробілами. Кожного разу, коли ви натискаєте `Добре` під час повторення, картка переходить до наступного етапу.

Наприклад, припустимо, що ваші інтервали вивчення встановлені на **1хв 10хв 1д**.

- Коли натискаєте `Знову`, картка повертається до першого етапу та буде показана приблизно через 1 хвилину.
- Коли натискаєте `Добре` на новій картці або картці, на яку відповідали `Знову`, вона переходить до наступного етапу та буде показана приблизно через 10 хвилин.
- Коли натискаєте `Добре` на картці після 10-хвилинного інтервалу, вона буде відкладена до наступного дня.
- Коли натискаєте `Добре` на картці наступного дня, вона закінчує етап вивчення (тобто вона завершує навчання) і стає карткою для повторення. Вона буде показана знову після затримки, налаштованої параметром _інтервалу завершення навчання_.

Якщо більше немає чого вивчати, Anki типово покаже картки до 20 хвилин раніше. Час для цього можна налаштувати в [параметрах](preferences.md).

Докладніше про роботу етапів та інтервалів див. у розділі [вивчення](studying.md#learningrelearning-cards).

#### Добові межі

Anki по-різному обробляє короткі інтервали та ті, що [перетинають добову межу](./preferences.md#review). Для коротких інтервалів картки показуються відразу після закінчення затримки, з пріоритетом над іншими, що очікують на повторення. Це робиться для того, щоб ви могли відповісти на картку якомога ближче до обраної вами затримки. Навпаки, якщо інтервал перетинає добову межу, він автоматично перетворюється на дні.

### Інтервал завершення навчання

Це затримка в днях між натисканням "Добре" на картці для вивчення, у якої закінчилися етапи, та наступним показом цієї картки вже як картки для повторення. Це означає, що цей інтервал є першим після того, як картка для вивчення стає карткою для повторення. Приклад можна знайти в попередньому розділі.

### Інтервал Легкості

Це затримка між натисканням `Легко` на картці для вивчення та її першим показом у режимі повторення.

Кнопка `Легко` відразу перетворює картку для вивчення на картку для повторення і призначає їй налаштовану затримку. Цей інтервал завжди має бути щонайменше таким же, як _інтервал завершення навчання_, і зазвичай трохи довшим.

### Порядок додавання

Цей параметр контролює, чи слід Anki додавати нові картки до колоди випадковим чином або у визначеному порядку. Коли змінюєте цю опцію, Anki пересортовує колоди, використовуючи налаштування поточної групи. Типово картки з меншим числом показуються першими під час навчання. Зміна цієї опції автоматично оновлює існуюче розташування нових карток.

Ось один нюанс режиму випадкового порядку: якщо ви переглянете багато нових карток, а потім додасте ще, новий матеріал статистично має більше шансів з’явитися раніше, ніж нові картки, які вже були в колоді. Наприклад, якщо у вас є 100 карток режимі випадкового порядку, а ви переглянули перші 50, нові картки все ще матимуть позиції з 1 по 100, але, оскільки ви вже переглянули перші 50, нові картки з більшою ймовірністю з'являться раніше. Щоб виправити це, можете змінити порядок на упорядкований режим і назад, щоб примусово пересортувати картки.

Коли ви обираєте випадковий порядок, Anki випадковізує ваші картки, зберігаючи картки одного типу близько одна до одної. Картки одного типу показуються в порядку, в якому з'являються їх типи, щоб дочірні картки вводилися послідовно. В іншому випадку, ви можете опинитися в ситуації, коли деякі типи карток будуть введені повністю, а інші — лише частково. Докладніше дивіться в розділах "приховані пов’язані картки" та "порядок відображення".

## Пропущені повторення

Коли забуваєте картку під час повторення, говорять, що картка "пропущена", і її потрібно знову вивчити. Типово поведінка для пропущених повторень полягає в тому, щоб скинути інтервал до 1 (тобто встановити термін на завтра) і помістити картку в чергу для повторення через 10 хвилин. Цю поведінку можна налаштувати за допомогою опцій, наведених нижче.

### Етапи повторного вивчення

Це те ж саме, що й 'етапи вивчення', але для пропущених повторень. Коли забуваєте картку (натискаєте `Знову`), вона переходить в фазу повторного вивчення, і перед тим як вона знову стане карткою для повторення, потрібно пройти всі інтервали повторного вивчення — або натиснути `Легко` на картці.

Якщо ви залишите етапи порожніми, картка пропустить повторне вивчення і отримає нову затримку повторення.

### Мінімальний інтервал

Визначає мінімальну кількість днів, які мають пройти після завершення повторного вивчення картки. Типово це один день, тобто після завершення повторного вивчення картка буде показана наступного дня.

### Приставучі картки (Leeches)

Налаштування обробки «приставучих карток» в Anki. Для отримання додаткової інформації дивіться розділ [приставучі картки](leeches.md).

## Порядок відображення

Опції в цьому розділі беруться з колоди, яку ви обираєте для навчання, а не з тої, до якої належить поточна картка.

Цей розділ доступний лише при ввімкненні [планувальника версії 3](https://faqs.ankiweb.net/the-2021-scheduler.html).

Додаткову інформацію про порядок відображення можна знайти в розділі [навчання](studying.md#display-order).

### Порядок збору нових карток

Керує тим, як Anki збирає картки з кожної дочірньої колоди. Доступні такі опції:

- Колода: збирає картки з кожної колоди по порядку, починаючи з верхньої. Картки з кожної колоди збираються в порядку зростання позиції. Якщо досягається денний ліміт вибраної колоди, збір може припинитися до того, як всі колоди будуть перевірені. Цей порядок найшвидший для великих колекцій і дозволяє надати пріоритет дочірній колоді, що знаходяться ближче до верху.

  Колоди/дочірні завжди впорядковуються за алфавітом, тому ви можете додати їм числовий префікс, як-от 001, щоб контролювати порядок їх відображення. Ви також можете використовувати `_` і `~` як префікси для розміщення елементів на початку або наприкінці списку.

  Хоча початковий порядок залежить від налаштування «Порядок Вставки», ви можете вручну [змінювати положення карток](https://docs.ankiweb.net/browsing.html#cards) різними способами.

- Колода, потім випадкові нотатки: збирає картки з кожної колоди по порядку, починаючи з верхньої. Картки з кожної колоди збираються випадковим чином.

- Висхідна позиція: збирає картки за висхідною позицією (номер запланованого показу), зазвичай найдавніше додані картки першими.

- Спадна позиція: збирає картки за спадною позицією (номер запланованого показу), зазвичай найновіше додані картки першими.

- Випадкові нотатки: збирає картки випадково обраних нотаток. Коли вимкнено приховування карток з однієї нотатки, це дозволяє побачити всі картки з однієї нотатки за один сеанс (наприклад, картки «спереду-назад» і «ззаду-наперед»).

- Випадкові картки: збирає картки повністю випадковим чином.

### Порядок сортування нових карток

Керує тим, як нові картки сортуються **після їх збирання**. Доступні такі опції:

- Тип картки: Показує картки в порядку за номером типу картки. Якщо у вас вимкнено приховування карток з нотатки одного типу, це забезпечить показ усіх карток типу «спереду-назад» до будь-яких карток типу «ззаду-назад». Це корисно для показу всіх карток з нотатки одного типу за один сеанс, але не надто близько одна до одної.

- Порядок збирання: Показує картки точно так, як вони були зібрані. Якщо приховування карток нотатки одного типу вимкнено, це зазвичай призведе до того, що всі картки одного типу будуть показані одна за одною.

- Тип картки, потім випадковий порядок: Як тип картки, але перемішує картки кожного номера типу картки. Якщо ви використовуєте висхідну позицію для збору найдавніших карток, ви можете скористатися цим налаштуванням, щоб побачити ці картки у випадковому порядку, але при цьому забезпечити, щоб картки нотатки одного типу не опинилися занадто близько одна до одної.

- Випадкові нотатки, потім тип картки: Випадковим чином вибирає нотатки, потім показує всі їхні картки у порядку.

- Випадковий порядок: Повністю перемішує зібрані картки.

### Пріоритет Нових Карток/Огляду

Керує тим, чи нові картки змішуються з оглядовими, чи показуються перед ними або після них.

### Пріоритет Карток з інтервалом між днями

Керує тим, чи картки з інтервалом в 1+ день змішуються з оглядовими картками, чи показуються перед ними або після них. Оскільки такі картки зазвичай важчі, ніж оглядові, деякі користувачі віддають перевагу показу їх наприкінці (щоб спочатку пройти легші завдання) або на початку (щоб було більше часу для повторення забутих карток).

### Порядок сортування оглядових карток

Керує тим, як сортуються оглядові картки під час огляду. Доступні такі опції:

- Дата показу, потім випадковий порядок: Типова опція, яка надає пріоритет карткам, які чекали найдовше, і є рекомендованою, коли ви встигли виконати всі огляди або маєте невелике відставання. Якщо ви взяли тривалу перерву або відстали в оглядах, варто тимчасово змінити порядок сортування.

- Дата показу, потім колода: Також надає пріоритет карткам, які чекали найдовше, а потім покаже оглядові картки для кожної дочірньої колоди по черзі.

- Колода, потім дата показу: Ця опція забезпечить показ оглядових карток для кожної дочірньої колоди по черзі. Зазвичай це не рекомендується, оскільки постійний показ матеріалу в однаковому порядку полегшує здогадування за контекстом, що може призвести до слабших результатів запам'ятовувань.

- Висхідні інтервали: Ця опція забезпечить показ карток із коротшими інтервалами першими.

- Спадні інтервали: Ця опція забезпечить показ карток із довшими інтервалами першими.

- Висхідна легкість: Ця опція покаже найскладніші картки першими.

- Спадна легкість: Ця опція дозволить спочатку працювати з легшими матеріалами.

- Відносна простроченість: Показує картки, які ви, найімовірніше, забули першими. Це корисно, якщо у вас велике відставання, на подолання якого знадобиться певний час, і ви хочете зменшити ймовірність забування більшої кількості карток.

  При використанні планувальника SM-2, простроченість визначається порівнянням того, наскільки картка прострочена, і як довго тривав інтервал. Наприклад, картка з поточним інтервалом 5 днів, яка прострочена на 2 дні, буде показана перед карткою з інтервалом 10 днів, яка прострочена на 3 дні.

  При використанні FSRS простроченість розраховується на основі коефіцієнта запам'ятовування кожної картки та бажаної затримки в налаштуваннях колоди.

## Timer

Anki monitors how long it takes you to answer each card, so that it
can show you how long was spent studying each day. The time taken does
not influence scheduling.

The options are:

- Maximum answer seconds: The default limit is 60 seconds. If you take
  longer than that, Anki assumes you have walked away from your computer
  or have been distracted, and limits the recorded time to 60 seconds, so
  that you don’t end up with inaccurate statistics. If you consistently
  take longer than 60 seconds to answer a card (from when question is shown
  until you press an answer button), you may want to either consider raising
  this limit, or, ideally, making your cards simpler.
- Show answer timer: In the review screen, show a timer that counts the number
  of seconds you're taking to review each card.
- Stop timer on answer: whether the timer should keep running when you show
  the answer.

## Auto Advance

Requires Anki 23.12 or later. Auto Advance allows you to automatically reveal
the answer and/or move to the next card. To use it, you must first set a non-zero
time in "seconds to show question" and/or "seconds to show answer". Then, in the
review screen, use the Auto Advance action from the `More` button to start advancing.

## Burying

When Anki gathers cards, it first gathers intraday learning cards, then interday learning cards, then reviews, and finally new cards. This affects how burying works:

- If you have all burying options enabled, the sibling that comes earliest in that list will be shown. For example, a review card will be shown in preference to a new card.
- Siblings later in the list can not bury earlier card types. For example, if you disable burying of new cards, and study a new card, it will not bury any interday learning or review cards, and you may see both a review sibling and new sibling in the same session.

The options are:

- Bury new siblings: whether other new cards of the same note (e.g., reverse cards, adjacent cloze deletions) will be delayed until the next day.
- Bury review siblings: whether other review cards of the same note will be delayed until the next day.
- Bury interday learning siblings: whether other learning cards of the same note with intervals >= 1 day will be delayed until the next day.

For more info about burying cards, please see [this section](./studying.md#siblings-and-burying) of the manual.

## Audio

By default, Anki automatically plays audio on the front and back of
cards. If you check _Don't play audio automatically_, Anki will not play
audio until you press the replay audio key, `r` or `F5`.

_Always include question side when replaying audio_ controls whether audio from
the question side should be played when replaying the audio while an answer is
shown. Please note that it does not control what happens when you show the
answer; for that please see [this section](templates/fields.md#special-fields).

## Advanced

### FSRS

The [Free Spaced Repetition Scheduler (FSRS)](https://github.com/open-spaced-repetition/fsrs4anki) is an alternative to Anki's legacy
SuperMemo 2 (SM2) scheduler. By more accurately determining when you are likely
to forget, it can help you remember more material in the same amount of time.
This setting is shared by all deck presets.

When you enable the setting, some new options will
become available, and SM-2 specific settings, such as "Graduating interval",
"Easy bonus", etc, will be hidden.

**Before Enabling**

- Please ensure all of your Anki clients support FSRS. Anki 23.10, AnkiMobile 23.10,
  and AnkiWeb all support it. AnkiDroid supports it in 2.17alpha3+. If
  one of your clients doesn't support it, things will not work correctly.
- If you previously used the 'custom scheduling' version of FSRS, please make
  sure you clear out the custom scheduling section before enabling FSRS.

#### FSRS Options

**Desired Retention**

Desired retention controls how likely you are to remember cards when they are reviewed.
The default value of 0.9 will schedule cards so you have a 90% chance of remembering
them when they come up for review again.

Here is a graph that shows how adjusting this value will affect your workload:

<img src="media/FSRS_retention.png" width="600">

There are two things to notice:

- As desired retention approaches 1.0, the frequency that you need to review cards
  increases drastically. For example, imagine you have a card that you have a 90%
  chance of remembering after 100 days. If your desired retention was 0.95, you'd
  need to review it after 47 days instead (approximately twice as frequently).
  At 0.97, the delay would be only 27 days (approximately 3.7x as frequently).
  At 0.99, you'd be reviewing every 9 days (more than 10x what you'd be doing with
  the defaults).

- As desired retention decreases, you'll forget a greater percentage of your
  cards, and those cards will need to be reviewed again. Eventually, you'll
  get to a point where the forgotten cards contribute more to your workload
  than you gain from the longer delays, which is why you see the workload
  on the left of the graph increasing. Also, bear in mind that forgetting
  material frequently is demotivating.

For these reasons, we suggest you be conservative when adjusting this
number, and recommend you keep it between 0.85 and 0.95.

**SM-2 retention**

If your actual retention before switching to FSRS was significantly different
from 0.9, adjusting this value will allow Anki to better estimate your memory
state when it encounters cards that are missing review logs. Since review
logs typically won't be missing unless you explicitly deleted them to free
up space, most users will not need to adjust this.

**FSRS parameters**

FSRS parameters affect how cards are scheduled. They are not intended to be
manually modified. Once you've accumulated 1000+ reviews, you can have Anki
optimize the parameters for you, based on your review history.

**Reschedule cards on change**

This option controls whether the due dates of cards will be changed when you
enable FSRS, or change the parameters. The default is not to reschedule
cards: future reviews will use the new scheduling, but there will be no
immediate change to your workload. If rescheduling is enabled, the due dates
of cards will be changed, often resulting in a large number of cards becoming
due, so **activating this option is not recommended** when first switching from SM2.

If you wish to visualize how FSRS would change your schedule without altering
your workload, there are two ways you can do so:

- Enable FSRS without rescheduling, and compare the interval and stability
  graphs. The interval graph will show the current intervals of cards; the stability
  graph will show the intervals FSRS would give cards if the desired retention is 0.9.
- Create a backup, enable FSRS with rescheduling, check the future due graph, and then
  undo or restore from the backup.

**Optimize FSRS parameters**

The FSRS optimizer uses machine learning to learn your memory patterns
and find parameters that best fit your review history. To do this, the optimizer
requires several reviews to fine-tune the parameters.

If you have less than 1,000 reviews, you can use the default parameters that
are already entered into the "FSRS parameters" field. Even with the default
parameters, FSRS should work well for most users.

Once you've done 1000+ reviews in Anki, you can use the `Optimize` button to
analyze your review history, and automatically generate parameters that are
optimal for your memory and the content you're studying. Parameters are
preset-specific, so if you have decks that vary wildly in difficulty, it
is recommended to assign them separate presets, as the parameters for easy
decks and hard decks will be different. There is no need to optimize your
parameters frequently - once every few months is sufficient.

By default, parameters will be calculated from the review history of all
decks using the current preset. You can optionally adjust the search
before calculating the parameters, if you'd like to alter which cards
are used for optimizing the parameters.

You can optimize the parameters for all of your presets at once, by clicking on the
down arrow in the top right, then choosing "Optimize all presets".

**Evaluate FSRS parameters**

You can use the `Evaluate` button in the "Optimize FSRS parameters"
section to see metrics that show how well the parameters in the
"Model parameters" field fit your review history. Smaller numbers
indicate a better fit to your review history.

Log-loss doesn't have an intuitive interpretation. RMSE (bins) can be
interpreted as the average difference between the predicted probability
of recalling a card (R) and the measured (from the review history)
probability. For example, RMSE=5% means that, on average, FSRS
is off by 5% when predicting R.

Note that log-loss and RMSE (bins) are not perfectly correlated,
so two decks may have similar RMSE values but very different log-loss values,
and vice-versa.

**Compute optimal retention**

This experimental tool assumes you're starting with 0 cards, and will
attempt to calculate the amount of material you'll be able to retain
in the given time frame. The estimated retention will greatly depend
on your inputs, and if it significantly differs from 0.9, it's a sign
that the time you've allocated each day is either too low or too high
for the amount of cards you're trying to learn. This number can be
useful as a reference, but it is not recommended to copy it into the
desired retention field.

#### Learning and Re-learning Steps

(Re)learning steps of 1+ days are not recommended when using FSRS. The main
reason they were popular with the old SM-2 scheduler is because repeatedly
failing a card after it has graduated from the learning phase could reduce
its ease a lot, leading to what some people called "ease hell". This is not
a problem that FSRS suffers from.  By keeping your learning steps under a
day, you will allow FSRS to schedule cards at times it has calculated are
optimum for your material and memory.  Another reason not to use longer
learning steps is because FSRS may end up scheduling the first review for a
shorter time than your last learning step, leading to the `Hard` button
showing a longer time than `Good`.

We also recommend you keep the number of learning steps to a minimum. Evidence
shows that repeating a card multiple times in a single day after you've
remembered it does not significantly help with memory, so your time is
better spent on other cards or a shorter study session

#### Add-On Compatibility

Some add-ons can cause conflicts with FSRS. As a general rule of thumb,
if an add-on affects a card's intervals, it shouldn't be used with FSRS.
A list of commonly used add-ons and their FSRS compatibility can be found in [Add-on Compatibility](https://github.com/open-spaced-repetition/fsrs4anki#add-on-compatibility).

#### More

For more info on FSRS, please check:

- [FSRS4Anki Wiki](https://github.com/open-spaced-repetition/fsrs4anki/wiki)
- [FSRS4Anki on Github](https://github.com/open-spaced-repetition/fsrs4anki)

### Maximum Interval

Allows you to place an upper limit on the time Anki
will wait to reshow a card. The default is 100 years; you can decrease
this to a smaller number if you’re willing to trade extra study time for
higher retention.

### Starting Ease

Controls the easiness that cards start out with. It is
set when a card graduates from learning for the first time. It defaults
to 2.50, meaning that once you have finished learning a card, answering
`Good` on subsequent reviews will increase the delay by approximately
2.5x (e.g. if the last delay was 10 days, the next delay would be around 25
days). Based upon how you rate the card in subsequent reviews, the
easiness may increase or decrease from its starting value.

### Easy Bonus

An extra multiplier applied to the interval when a review card is answered
`Easy`. With the default value of 1.30, `Easy` will give an interval that is
1.3 times the `Good` interval (e.g. if the Good interval was 10 days, the Easy
interval would be around 13 days).

### Interval Modifier

An extra multiplier that is applied to all reviews. At its default of 1.00 it
does nothing. If you set it to 0.80, though, for example, intervals will be generated at
80% of their normal size (so a 10 day interval would become 8 days). You can
thus use the multiplier to make Anki present cards more or less frequently than
it would otherwise, trading study time for retention or vice versa.

For moderately difficult material, the average user should find they
remember approximately 90% of mature cards that come up for review. You
can find out your own performance by opening the graphs/statistics for a
deck and looking at the Answer Buttons graph - mature retention is the
correct% on the right side of the graph. If you haven’t been studying
long, you may not have any mature cards yet. As performance with new
cards and younger cards can vary considerably, it’s a good idea to wait
until you have a reasonable amount of mature reviews before you start
drawing conclusions about your retention rate.

On the SuperMemo website, they suggest that you can find an appropriate
multiplier for a desired retention rate. Their formula boils down to:

    log(desired retention%) / log(current retention%)

Imagine we have a current retention rate of 85% and we want to increase
it to 90%. We’d calculate the modifier as:

    log(90%) / log(85%) = 0.65

You can use Google to [calculate it](https://www.google.com/search?q=log(90%25)+%2F+log(85%25)) for you.

If you plug the resulting 65% into the interval modifier, you should
find over time that your retention moves closer to your desired
retention.

One important thing to note however is that the trade-off between time
spent studying and retention is not linear: we can see here that to
increase our retention by 5 percentage points, we would have to study 35%
more frequently. If the material you are learning is very important then
it may be worth the extra effort – that is, of course, something you will need to
decide for yourself. If you are simply worried that you are forgetting too
much, then you may find investing more time at the initial learning stage
and/or using mnemonics will give you more gain for less effort.

One final thing to note is that Anki forces a new interval to be at
least 1 day longer than it was previously, so that you do not get stuck
reviewing with the same interval forever. If your goal is to repeat a
card once a day for multiple days, you can do that by setting more
learning mode steps, instead of by adjusting this modifier.

### Hard Interval

The multiplier used when you use the `Hard` button. The percentage is relative
to the previous interval: e.g. with a default of 1.20, a card with a 10-day interval
will be given 12 days.

### New Interval

The multiplier used when you use the `Again` button on a review card. The
default 0.00 means that a review card's delay is reset to zero when you forget it
(which then becomes 1 day after the [minimum interval](#minimum-interval) is
applied).

If changed from the default, it is possible for forgotten cards to preserve part
of their previous delay. For example, if a card had a 100 day interval, and you set
the _New Interval_ to 0.20, the new interval would be 20 days.

While preserving part of the interval may seem to make sense, SuperMemo has observed
that preserving part of the delay can actually [be counter-productive](https://supermemo.guru/wiki/Post-lapse_stability). For this reason, we recommend you leave it on the default setting.

## Custom Scheduling

Please see [this page](https://faqs.ankiweb.net/the-2021-scheduler.html#add-ons-and-custom-scheduling).

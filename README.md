# FD DayZ Layout Visual Editor PRO — повна інструкція від A до Я

Цей документ описує повну історію розробки та використання **FD DayZ Layout Visual Editor PRO**, починаючи з першої тестової версії і до версії **V24 TREE + STYLES + TEMPLATES**.

Редактор створений для роботи з GUI `.layout` файлами DayZ. Він відкривається прямо в браузері як HTML-файл і дозволяє візуально редагувати позиції, розміри, кольори, тексти, кнопки, панелі, списки, ItemPreviewWidget та інші елементи DayZ GUI.

---

# 1. Що це за програма

**FD DayZ Layout Visual Editor PRO** — це візуальний редактор DayZ GUI layout-файлів.

Він потрібен для того, щоб не редагувати `.layout` тільки вручну в тексті, а бачити GUI приблизно так, як він буде виглядати в грі.

Редактор допомагає:

- відкривати `.layout`;
- бачити структуру widgets;
- рухати елементи мишкою;
- змінювати розмір;
- редагувати колір і прозорість;
- бачити текст, кнопки, панелі;
- перевіряти layout у режимі Game Preview;
- аналізувати прозорість через Inspector PRO;
- працювати з assets;
- використовувати шаблони;
- групувати widgets;
- копіювати стилі;
- готувати layout для DayZ мода.

---

# 2. Для чого він створювався

Спочатку задача була проста: зробити інструмент, який може відкрити DayZ `.layout` і показати його візуально.

Проблема була така:

- Workbench не завжди зручний;
- редагувати `.layout` вручну важко;
- позиції й розміри треба постійно тестувати в грі;
- прозорість у редакторі й у грі може виглядати по-різному;
- частина GUI-елементів не видно, якщо неправильно задані `position`, `size`, `alpha`, `halign`, `valign`;
- потрібен швидкий інструмент для меню штрафстоянки, craft preview, NPC-меню, гаража, трейдера та інших DayZ GUI.

---

# 3. Коротка історія розробки

## V1 — перша тестова версія

Перша версія була простим HTML-файлом.

Вона вміла:

- відкривати `.layout`;
- показувати базові widgets;
- рухати блоки мишкою;
- міняти розмір;
- копіювати готовий layout назад.

Це була тестова основа, щоб перевірити саму ідею.

---

## V2 — фікс відкриття `fd_craft_preview.layout`

У V1 були проблеми з відкриттям деяких layout-файлів.

У V2 було додано:

- покращений parser `.layout`;
- drag & drop;
- повідомлення про помилки;
- автоматичний приклад для craft preview layout.

---

## V3 — відкриття будь-якого layout

У V3 було змінено логіку:

- редактор більше не відкривав автоматично один конкретний файл;
- користувач сам вибирає будь-який `.layout`;
- можна перетягувати layout у вікно;
- можна редагувати різні GUI-файли.

Це зробило редактор універсальним.

---

## V4 — PRO-версія

У V4 редактор став схожим на справжню програму.

Було додано:

- дерево widgets;
- інспектор;
- grid;
- snap;
- zoom;
- undo / redo;
- додавання widgets;
- видалення widgets;
- дублювання;
- front / back;
- гарячі клавіші;
- експорт `.layout`.

---

## V5 — Circular JSON Fix

У V4 була помилка:

```text
Converting circular structure to JSON
```

Вона виникала через `parent`-посилання в дереві widgets.

У V5 було виправлено:

- Undo / Redo;
- дублювання widgets;
- збереження історії без circular structure.

---

## V6 — Relative Layout Fix

Частина DayZ layout використовує відносні координати:

```text
position 0.08 0.08
size 0.84 0.78
```

V5 сприймав такі значення як пікселі, і layout міг бути майже невидимим.

У V6 було додано підтримку:

```text
hexactpos
vexactpos
hexactsize
vexactsize
```

---

## V7 — Auto Relative Fix

У деяких layout-файлах відносні координати були вказані без exact-флагів.

V7 навчився автоматично розуміти:

```text
0.08
0.84
0.5
1
```

як relative values, якщо exact-флаг не прописаний.

Також було покращено:

- кольори;
- alpha 0-255;
- text color;
- `halign`;
- `valign`.

---

## V8 — Anchor Fix

У layout `fdis_impound_menu.layout` слово `ЭВАКУАТОР` частково не показувалось.

Причина: DayZ використовує `halign right` як прив’язку самого widget, а редактор враховував тільки вирівнювання тексту.

У V8 було виправлено:

- `halign right`;
- `halign center`;
- `valign bottom`;
- `valign center`.

---

## V9 — UI Tools

У V9 було додано більше інструментів інтерфейсу:

- теми редактора;
- список DayZ-шрифтів;
- Center X;
- Center Y;
- Center;
- Safe Area;
- покращений preview blur / panel стилів.

---

## V10 — Neon 3D UI

У V10 було перероблено зовнішній вигляд самого редактора.

Додано:

- 3D-кнопки;
- неонова підсвітка;
- перемикач Neon ON / OFF;
- вибір кольору акценту;
- красивіший glow панелей і сцени.

---

## V11 — Game Preview

У V11 було додано режим:

```text
Game Preview
```

Він дозволяє бачити layout ближче до вигляду в грі.

Додано:

- приховання редакторських рамок;
- приховання resize handles;
- canvas 1920x1080;
- можливість завантажити скрін із DayZ як фон;
- готові фони: grass, forest, night, inventory.

---

## V12 — No Game Note

У V11 внизу показувався службовий напис:

```text
V11 Game Preview: можно загрузить свой скрин из DayZ как фон
```

У V12 цей напис було прибрано.

---

## V13 — True DayZ Transparency

У грі layout виглядав прозоріше, ніж у редакторі.

V13 додав режим:

```text
True Alpha ON / OFF
```

Цей режим прибирає fake glow / fake shadow і показує прозорість ближче до реального DayZ.

---

## V14 — Game Buttons

У V14 було перероблено preview кнопок, щоб вони виглядали ближче до кнопок DayZ.

Додано:

- темно-сірий стиль кнопок;
- верхній блік;
- м’яка рамка;
- білий текст із тінню.

---

## V15 — In-game Highlight

У V15 було додано підсвічування, ближче до DayZ.

Додано:

- glow для заголовків;
- glow для секцій;
- кращий вигляд labels;
- темні / скляні панелі;
- Game Glow ON / OFF.

---

## V16 — Color Hover

Користувач попросив, щоб не тільки кнопка "Оновити", а всі widgets підсвічувались при наведенні.

У V16 додано:

- hover glow для всіх widgets;
- колір hover береться із `color` / `textColor`;
- працює для text, buttons, panels, image, item preview.

---

## V17 — Uniform Buttons

Зелена кнопка "Оновити" виглядала окремо від інших.

У V17 було прибрано:

- автоматичний зелений стиль;
- Button Accent;
- Button state.

Тепер усі кнопки виглядають однаково.

---

## V18 — Asset Viewer

У V18 було додано відкриття інших GUI / asset файлів.

Підтримуються:

```text
.png
.jpg
.jpeg
.webp
.gif
.bmp
.svg
.layout
.json
.xml
.cpp
.c
.h
.rvmat
.emat
.txt
.csv
.paa
.edds
.tga
```

Asset Viewer дозволяє:

- переглядати картинки;
- читати текстові файли;
- бачити `.paa` / `.edds` як DayZ texture assets;
- ставити PNG/JPG/WEBP як фон Game Preview.

---

## V19 — Responsive Topbar

Через велику кількість кнопок верхня панель почала обрізатись.

У V19 було зроблено:

- адаптивний toolbar;
- перенос кнопок на новий ряд;
- автоматичну висоту верхньої панелі;
- компактніші кнопки й select-поля.

---

## V20 — PAA / EDDS Preview Helper

Браузер не може напряму показати `.paa` / `.edds`.

У V20 додано helper:

```text
button_bg.paa
button_bg.png
```

Якщо поруч є PNG/JPG/WEBP з такою самою назвою, редактор показує його як preview для `.paa` / `.edds`.

---

## V21 — Layout Inspector PRO

У V21 редактор почав сам знаходити проблеми layout.

Inspector PRO перевіряє:

- занадто прозорі панелі;
- нульовий або маленький size;
- текст, який може обрізатися;
- маленький ItemPreviewWidget;
- widgets за межами layout;
- buttons без text.

Додано:

- Auto Fix Alpha;
- Copy Report;
- вибір першої проблеми;
- Hide selected;
- Lock selected;
- Align tools;
- Color Picker.

---

## V22 — MultiSelect + Guides

У V22 додано:

- MultiSelect;
- Ctrl / Shift + Click;
- рамка виділення;
- рух групи widgets;
- guides;
- snap до країв і центру;
- snap до інших widgets;
- жовта рамка multi-selected;
- рух групи стрілками.

---

## V23 — Group + Distribute

У V23 додано:

- Dist H;
- Dist V;
- Group;
- Ungroup;
- spacing labels;
- `Ctrl + G`;
- `Ctrl + Shift + G`.

Це дозволяє рівномірно розкладати кнопки й об’єднувати групи widgets.

---

## V24 — Tree + Styles + Templates

V24 — поточна основна версія.

Додано:

- Tree Collapse / Expand;
- Smart Copy Style;
- Smart Paste Style;
- Template Presets;
- Distance Measure;
- NPC Menu template;
- Vehicle Card template;
- Button Row template;
- Notify Popup template.

---

# 4. Як завантажити й запустити

## Крок 1 — Завантажити архів

Файл:

```text
FD_DayZ_Layout_Visual_Editor_PRO_V24_TREE_STYLES_TEMPLATES.zip
```

## Крок 2 — Розпакувати

Розпакувати ZIP у будь-яку папку, наприклад:

```text
D:\DayZ_Tools\FD_DayZ_Layout_Visual_Editor\
```

## Крок 3 — Відкрити HTML

Відкрити файл:

```text
FD_DayZ_Layout_Visual_Editor_PRO_V24_TREE_STYLES_TEMPLATES.html
```

Можна відкривати в:

- Google Chrome;
- Microsoft Edge;
- Opera;
- Firefox.

Рекомендовано Chrome або Edge.

---

# 5. Як відкрити layout

1. Натиснути кнопку:

```text
Открыть .layout
```

2. Вибрати файл, наприклад:

```text
fdis_impound_menu.layout
fd_craft_preview.layout
my_custom_menu.layout
```

3. Після відкриття з’явиться:

- зліва — дерево widgets;
- по центру — сцена;
- справа — інспектор.

---

# 6. Основні частини інтерфейсу

## Верхня панель

Тут знаходяться кнопки:

```text
Открыть .layout
Открыть GUI/Assets
Inspector PRO
MultiSelect
Guides
Game Preview
True Alpha
Game Glow
Color Hover
Скачать
Копировать
Undo
Redo
Zoom
Grid
Snap
Safe Area
Neon
Theme
Preset
```

## Ліва панель

Містить:

- дерево widgets;
- пошук;
- buttons для delete / duplicate / hide / lock;
- align tools;
- group tools;
- templates.

## Центральна сцена

Тут видно layout.

Можна:

- клікати;
- рухати;
- resize;
- виділяти кілька widgets;
- бачити guides;
- бачити Game Preview.

## Права панель

Інспектор властивостей.

Можна змінювати:

```text
Name
Type
Position
Size
Color
Text
Font
Text color
Priority
Visible
Exact flags
```

---

# 7. Як редагувати widget

## Вибрати widget

Клікнути по ньому на сцені або в дереві.

## Перемістити

Затиснути мишкою і перетягнути.

## Змінити розмір

Потягнути за жовтий кут.

## Змінити текст

У правій панелі знайти поле:

```text
Text
```

і змінити напис.

## Змінити колір

У правій панелі змінити:

```text
Color RGBA
```

або використати Color Picker.

---

# 8. Як працює alpha / прозорість

Приклад:

```text
color 0 0 0 0.55
```

Означає:

- `0 0 0` — чорний колір;
- `0.55` — 55% непрозорості.

Якщо в грі меню занадто прозоре, треба підняти alpha:

```text
color 0 0 0 0.85
```

або:

```text
color 0 0 0 0.95
```

Для перевірки використовуй:

```text
True Alpha ON
Inspector PRO
Auto Fix Alpha
```

---

# 9. Як працює MultiSelect

## Вибрати кілька widgets

```text
Ctrl + Click
Shift + Click
Cmd + Click
```

Або протягнути рамку по пустому місцю сцени.

## Що можна робити з групою

- рухати;
- видаляти;
- дублювати;
- вирівнювати;
- робити Copy / Paste Style;
- Group / Ungroup;
- Dist H / Dist V.

---

# 10. Як працюють Guides

Guides показують зелені лінії при перетягуванні.

Snap відбувається до:

- країв сцени;
- центру сцени;
- країв widgets;
- центру widgets.

Можна вимкнути:

```text
Guides OFF
Snap OFF
```

---

# 11. Dist H / Dist V

## Dist H

Для рівномірного розкладання по горизонталі.

1. Виділити 3 або більше widgets.
2. Натиснути:

```text
Dist H
```

Перший і останній лишаються на місці, середні розподіляються між ними.

## Dist V

Те саме по вертикалі.

```text
Dist V
```

---

# 12. Group / Ungroup

## Group

1. Виділити кілька widgets.
2. Натиснути:

```text
Group
```

Widgets будуть об’єднані в wrapper group.

## Ungroup

1. Вибрати group wrapper.
2. Натиснути:

```text
Ungroup
```

Гарячі клавіші:

```text
Ctrl + G
Ctrl + Shift + G
```

---

# 13. Copy Style / Paste Style

## Copy Style

Копіює стиль одного widget:

```text
color
textColor
font
textSize
priority
style
halign
valign
```

## Paste Style

Застосовує стиль до selected widgets.

Приклад:

1. Вибрати кнопку.
2. Натиснути `Copy Style`.
3. Виділити інші кнопки.
4. Натиснути `Paste Style`.

Гарячі клавіші:

```text
Ctrl + Shift + C
Ctrl + Shift + V
```

---

# 14. Tree Collapse / Expand

У дереві можна згортати і розгортати groups.

Кнопки:

```text
Collapse
Expand
```

Так зручніше працювати з великими layout.

---

# 15. Templates

V24 має готові шаблони:

```text
NPC Menu
Vehicle Card
Button Row
Notify Popup
```

## NPC Menu

Шаблон для NPC-меню.

## Vehicle Card

Шаблон картки транспорту.

## Button Row

Шаблон ряду кнопок.

## Notify Popup

Шаблон повідомлення.

Після додавання шаблон можна редагувати як звичайну group.

---

# 16. Inspector PRO

Відкривається кнопкою:

```text
Inspector PRO
```

## Аналіз layout

Натиснути:

```text
Аналізувати layout
```

Редактор покаже проблеми.

## Auto Fix Alpha

Натиснути:

```text
Auto Fix Alpha
```

Редактор підніме прозорість темних панелей.

## Copy Report

Копіює звіт про проблеми.

---

# 17. Game Preview

Кнопка:

```text
Game Preview
```

У цьому режимі:

- ховаються рамки редактора;
- ховаються resize handles;
- layout виглядає чистіше;
- можна перевірити вигляд на фоні гри.

## Фон із гри

Натиснути:

```text
Фон игры
```

Вибрати screenshot з DayZ.

Підтримується:

```text
.png
.jpg
.webp
```

---

# 18. True DayZ Transparency

Кнопка:

```text
True Alpha ON
```

Цей режим показує прозорість ближче до гри.

Якщо в цьому режимі фон занадто прозорий — треба змінити `color alpha`.

---

# 19. Color Hover

Кнопка:

```text
Color Hover ON
```

При наведенні курсора widget підсвічується своїм кольором.

---

# 20. Asset Viewer

Кнопка:

```text
Открыть GUI/Assets
```

Підтримуються:

```text
.png
.jpg
.jpeg
.webp
.gif
.bmp
.svg
.layout
.json
.xml
.cpp
.c
.h
.rvmat
.emat
.txt
.csv
.paa
.edds
.tga
```

---

# 21. PAA / EDDS Preview Helper

Браузер не може напряму показувати:

```text
.paa
.edds
```

Тому використовується PNG-пара.

Приклад:

```text
button_bg.paa
button_bg.png
```

Відкрий обидва файли через Assets, і редактор покаже PNG як preview для PAA.

---

# 22. ItemPreviewWidget

У браузері `ItemPreviewWidget` показується як:

```text
ITEM PREVIEW
```

Це нормально.

Справжню 3D-модель покаже тільки DayZ.

---

# 23. Як зберегти layout

Натиснути:

```text
Скачать
```

Редактор завантажить edited `.layout`.

Потім:

1. Замінити layout у моді.
2. Перепакувати PBO.
3. Перевірити в DayZ.

---

# 24. Рекомендований workflow

1. Зробити backup старого `.layout`.
2. Відкрити layout у редакторі.
3. Внести зміни.
4. Увімкнути Game Preview.
5. Увімкнути True Alpha.
6. Запустити Inspector PRO.
7. Якщо потрібно — Auto Fix Alpha.
8. Перевірити Guides.
9. Перевірити Distance.
10. Натиснути Скачать.
11. Замінити layout у моді.
12. Перепакувати PBO.
13. Запустити DayZ.
14. Перевірити в грі.

---

# 25. Гарячі клавіші

```text
Ctrl + Z = Undo
Ctrl + Y = Redo
Delete = Delete selected
Ctrl + G = Group
Ctrl + Shift + G = Ungroup
Ctrl + Shift + C = Copy Style
Ctrl + Shift + V = Paste Style
Arrow keys = Move selected
Shift + Arrow keys = Resize selected
Ctrl + Arrow keys = Bigger move step
```

---

# 26. Публікація на GitHub

## Рекомендована структура репозиторію

```text
FD_DayZ_Layout_Visual_Editor/
├── README.md
├── LICENSE
├── editor/
│   └── FD_DayZ_Layout_Visual_Editor_PRO_V24_TREE_STYLES_TEMPLATES.html
├── examples/
│   └── example_menu.layout
├── docs/
│   └── screenshots/
└── CHANGELOG.md
```

## Опис репозиторію

```text
Visual browser-based DayZ GUI .layout editor with Game Preview, Inspector PRO, MultiSelect, Guides, Templates, Asset Viewer and PAA/EDDS Preview Helper.
```

## Topics

```text
dayz
dayz-mod
dayz-tools
layout-editor
gui-editor
modding
enfusion
paa
edds
visual-editor
html-editor
```

---

# 27. Обмеження

Редактор не є повною заміною Workbench.

Обмеження:

- не рендерить справжні 3D-моделі DayZ;
- не декодує напряму `.paa` / `.edds`;
- ItemPreviewWidget показує placeholder;
- фінальний результат треба перевіряти в DayZ.

---

# 28. Рекомендовані інструменти поруч

```text
Visual Studio Code
Notepad++
DayZ Tools
Addon Builder
PBO Manager
TexView2
PAA Image Tool
ImageToPAA
Noesis
```

---

# 29. License

Рекомендована ліцензія:

```text
MIT License
```

---

# 30. Credits

Created for DayZ modding and GUI layout editing.


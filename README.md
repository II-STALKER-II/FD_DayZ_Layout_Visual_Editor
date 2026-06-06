# FD DayZ Layout Visual Editor PRO

**FD DayZ Layout Visual Editor PRO** — це візуальний HTML-редактор для GUI `.layout` файлів DayZ.

Програма дозволяє відкривати, переглядати й редагувати DayZ layout-файли без постійного запуску Workbench. Редактор працює прямо в браузері та підходить для створення меню, HUD-вікон, NPC-меню, меню трейдера, штрафстоянки, гаража, craft preview, кнопок, списків, карток транспорту та інших GUI-елементів DayZ.

---

## Що вміє редактор

### Основні можливості

* Відкриття `.layout` файлів DayZ
* Візуальне редагування GUI
* Переміщення елементів мишкою
* Зміна розміру елементів
* Редагування позиції, розміру, кольору, тексту, прозорості
* Підтримка `PanelWidget`, `TextWidget`, `ButtonWidget`, `ImageWidget`, `ItemPreviewWidget`, `FrameWidget`
* Дерево всіх widgets
* Інспектор властивостей
* Експорт назад у `.layout`
* Copy layout code
* Робота повністю локально в браузері

---

## Основні функції

### Visual Editor

Редактор показує GUI-вікно на сцені. Кожен widget можна вибрати, рухати, змінювати розмір і редагувати через праву панель.

Можна редагувати:

```text
name
type
position
size
color
text
font
text color
text size
priority
visible
ignore pointer
clip children
halign
valign
hexactpos
vexactpos
hexactsize
vexactsize
```

---

## Як запустити

1. Завантажити архів:

```text
FD_DayZ_Layout_Visual_Editor_PRO_V24_TREE_STYLES_TEMPLATES.zip
```

2. Розпакувати ZIP у будь-яку папку.

3. Відкрити HTML-файл:

```text
FD_DayZ_Layout_Visual_Editor_PRO_V24_TREE_STYLES_TEMPLATES.html
```

4. Редактор відкриється у браузері.

5. Натиснути:

```text
Открыть .layout
```

6. Вибрати потрібний DayZ layout-файл.

---

## Як користуватись

### Відкрити layout

Натисни кнопку:

```text
Открыть .layout
```

Після цього вибери файл, наприклад:

```text
fdis_impound_menu.layout
fd_craft_preview.layout
my_custom_menu.layout
```

Після відкриття ти побачиш:

```text
зліва — дерево widgets
по центру — візуальне вікно layout
справа — інспектор властивостей
```

---

## Редагування елементів

### Перемістити widget

1. Клікни по елементу.
2. Затисни ліву кнопку миші.
3. Перетягни в потрібне місце.

### Змінити розмір

1. Вибери widget.
2. Потягни за жовтий кут.
3. Розмір зміниться.

### Точне редагування

У правій панелі можна вручну прописати:

```text
Position X / Y
Size W / H
Color RGBA
Text
Priority
Visible
```

---

## Color Picker

У редакторі є зручний вибір кольору.

Можна вибрати колір мишкою, а alpha-прозорість окремо виставити в полі `A`.

Приклад кольору:

```text
color 0 0 0 0.85
```

Де:

```text
0 0 0 = чорний колір
0.85 = прозорість
```

---

## MultiSelect

Редактор підтримує вибір кількох widgets одночасно.

### Як вибрати кілька елементів

```text
Ctrl + Click
Shift + Click
Cmd + Click
```

Або потягни мишкою по пустому місцю сцени — з’явиться рамка виділення.

### Що можна робити з групою

```text
рухати
видаляти
дублювати
вирівнювати
міняти розмір
копіювати стиль
застосовувати стиль
групувати
розгруповувати
```

---

## Guides і Snap

Редактор має направляючі лінії.

Вони допомагають рівно виставляти widgets.

Snap працює до:

```text
країв сцени
центру сцени
країв інших widgets
центру інших widgets
```

Кнопки:

```text
Guides ON / OFF
Snap ON / OFF
```

---

## Dist H / Dist V

### Dist H

Рівномірно розкладає selected widgets по горизонталі.

Потрібно виділити мінімум 3 елементи.

```text
Dist H
```

### Dist V

Рівномірно розкладає selected widgets по вертикалі.

```text
Dist V
```

---

## Group / Ungroup

### Group

Об’єднує кілька widgets у group wrapper.

```text
Group
```

Після цього групу можна рухати як один блок.

### Ungroup

Розпаковує group wrapper назад.

```text
Ungroup
```

Гарячі клавіші:

```text
Ctrl + G = Group
Ctrl + Shift + G = Ungroup
```

---

## Copy Style / Paste Style

Можна скопіювати стиль одного widget і застосувати до інших.

### Copy Style копіює:

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

### Як користуватись

1. Вибери кнопку або текст.
2. Натисни:

```text
Copy Style
```

3. Виділи інші widgets.
4. Натисни:

```text
Paste Style
```

Гарячі клавіші:

```text
Ctrl + Shift + C = Copy Style
Ctrl + Shift + V = Paste Style
```

---

## Tree Collapse / Expand

У дереві widgets можна згортати й розгортати елементи.

```text
Collapse
Expand
```

Це зручно для великих layout-файлів, де багато вкладених елементів.

---

## Templates

У редакторі є готові шаблони:

```text
NPC Menu
Vehicle Card
Button Row
Notify Popup
```

Шаблон додається як готова група widgets. Його можна рухати, редагувати, змінювати текст, кольори й розміри.

---

## Layout Inspector PRO

Inspector PRO допомагає знайти проблеми layout до запуску гри.

Кнопка:

```text
Inspector PRO
```

### Що перевіряє

```text
занадто прозорі panel/frame
нульовий або дуже маленький size
текст, який може обрізатися
маленький ItemPreviewWidget
widgets за межами layout
buttons без text
```

### Auto Fix Alpha

Якщо в грі меню занадто прозоре, можна натиснути:

```text
Auto Fix Alpha
```

Редактор підніме alpha у занадто прозорих темних панелей.

---

## Game Preview

Кнопка:

```text
Game Preview
```

Цей режим показує layout ближче до того, як він буде виглядати в DayZ.

У Game Preview:

```text
ховаються рамки редактора
ховаються resize handles
layout виглядає чистіше
можна поставити скрін із гри як фон
```

---

## Фон із гри

Можна завантажити власний скрін із DayZ як фон.

1. Натисни:

```text
Фон игры
```

2. Вибери картинку:

```text
.png
.jpg
.webp
```

3. Увімкни:

```text
Game Preview
```

Так можна перевірити, як меню виглядатиме прямо на фоні гри.

---

## True DayZ Transparency

Кнопка:

```text
True Alpha ON / OFF
```

Цей режим показує прозорість ближче до DayZ.

Якщо в цьому режимі панелі занадто прозорі — треба підняти alpha в `color`.

Приклад:

```text
color 0 0 0 0.55
```

можна змінити на:

```text
color 0 0 0 0.85
```

---

## Color Hover

Кнопка:

```text
Color Hover ON / OFF
```

При наведенні курсора widget підсвічується кольором, який прописаний у нього в layout.

---

## Asset Viewer

Кнопка:

```text
Открыть GUI/Assets
```

Дозволяє відкривати додаткові GUI-файли й assets.

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

## PAA / EDDS Preview Helper

Браузер не може напряму показувати:

```text
.paa
.edds
```

Тому редактор використовує PNG preview pair.

### Приклад

```text
button_bg.paa
button_bg.png
```

Якщо відкрити обидва файли через Asset Viewer, редактор покаже `button_bg.png` як preview для `button_bg.paa`.

У самому DayZ layout можна залишати шлях до `.paa`.

---

## ItemPreviewWidget

`ItemPreviewWidget` у браузері показується як placeholder:

```text
ITEM PREVIEW
```

Це нормально, бо браузер не може рендерити справжню 3D-модель DayZ.

У грі `ItemPreviewWidget` буде працювати через DayZ, якщо layout і скрипт налаштовані правильно.

---

## Гарячі клавіші

```text
Ctrl + Z = Undo
Ctrl + Y = Redo
Delete = видалити selected widget
Ctrl + G = Group
Ctrl + Shift + G = Ungroup
Ctrl + Shift + C = Copy Style
Ctrl + Shift + V = Paste Style
Arrow keys = рухати selected widget
Shift + Arrow keys = змінювати розмір
Ctrl + Arrow keys = рухати більшим кроком
```

---

## Як зберегти layout

Після редагування натисни:

```text
Скачать
```

Редактор завантажить edited `.layout`.

Потім треба замінити старий файл layout у твоєму DayZ моді.

Приклад шляху:

```text
MyMod/gui/layouts/my_menu.layout
```

Після цього перепакуй PBO і перевір у грі.

---

## Рекомендований workflow

1. Зробити backup старого `.layout`.
2. Відкрити layout у редакторі.
3. Внести зміни.
4. Увімкнути Game Preview.
5. Увімкнути True Alpha.
6. Запустити Inspector PRO.
7. Якщо треба — Auto Fix Alpha.
8. Перевірити Guides і Distance.
9. Натиснути Скачать.
10. Замінити layout у моді.
11. Перепакувати PBO.
12. Перевірити в DayZ.

---

## Публікація на GitHub

Рекомендована структура:

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

---

## Опис для GitHub

```text
Visual browser-based DayZ GUI .layout editor with Game Preview, Inspector PRO, MultiSelect, Guides, Templates, Asset Viewer and PAA/EDDS Preview Helper.
```

---

## Topics для GitHub

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

## Обмеження

Редактор не є повною заміною Workbench.

Обмеження:

```text
не рендерить справжні 3D-моделі DayZ
не декодує напряму .paa / .edds
ItemPreviewWidget показується як placeholder
фінальний результат завжди треба перевіряти в DayZ
```

---

## Рекомендовані інструменти поруч

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

## License

Рекомендована ліцензія:

```text
MIT License
```

---

## Credits

Created for DayZ modding and GUI layout editing.

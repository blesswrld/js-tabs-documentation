
# JavaScript Tabs Module 🗂️

**JavaScript Tabs Module** предоставляет компонент для создания вкладок на веб-странице. Этот модуль позволяет легко управлять содержимым вкладок, скрывая и показывая соответствующие элементы при переключении между ними.

---

## Основные особенности

1. **Переключение между вкладками**: Легко переключайте вкладки с использованием простых кликов.
2. **Анимация содержимого вкладок**: Плавное добавление и удаление контента вкладки с использованием CSS классов.
3. **Настройка активной вкладки**: Возможность указать класс для активной вкладки для выделения её визуально.
4. **Обработка кликов**: Обработчик кликов на родительский элемент вкладок для переключения активных вкладок.

---

## Установка

1. Клонируйте репозиторий:
   ```bash
   git clone https://github.com/yourusername/js-tabs-module.git
   ```

2. Или просто скачайте файл `tabs.js` и включите его в ваш проект.

---

## Быстрый старт

### Пример HTML-разметки

Убедитесь, что ваш HTML код для вкладок имеет такую структуру:

```html
<!-- Родительский элемент вкладок -->
<div class="tabheader__items">
    <div class="tabheader__item">Вкладка 1</div>
    <div class="tabheader__item">Вкладка 2</div>
    <div class="tabheader__item">Вкладка 3</div>
</div>

<!-- Контент вкладок -->
<div class="tabcontent">Контент для вкладки 1</div>
<div class="tabcontent">Контент для вкладки 2</div>
<div class="tabcontent">Контент для вкладки 3</div>
```

### Инициализация JavaScript

Инициализируйте вкладки, импортировав модуль `tabs.js` и передав необходимые селекторы и активный класс:

```javascript
import tabs from './modules/tabs.js';

tabs('.tabheader__item', '.tabcontent', '.tabheader__items', 'tabheader__item_active');
```

---

## Пример использования

Вот как работает модуль вкладок:

- **Переключение между вкладками**: Модуль позволяет пользователям переключаться между вкладками, скрывая/показывая соответствующие элементы.
- **Настройка активной вкладки**: Укажите класс для активной вкладки, чтобы выделить её на странице.
- **Плавное отображение содержимого**: Вкладки плавно отображаются и скрываются с помощью CSS анимации.

```javascript
// Основная функция для переключения вкладок
function tabs(tabsSelector, tabsContentSelector, tabsParentSelector, activeClass) {
    let tabs = document.querySelectorAll(tabsSelector),
        tabsContent = document.querySelectorAll(tabsContentSelector),
        tabsParent = document.querySelector(tabsParentSelector);

    function hideTabContent() {
        tabsContent.forEach(item => {
            item.classList.add('hide');
            item.classList.remove('show', 'fade');
        });

        tabs.forEach(item => {
            item.classList.remove(activeClass);
        });
    }

    function showTabContent(i = 0) {
        tabsContent[i].classList.add('show', 'fade');
        tabsContent[i].classList.remove('hide');
        tabs[i].classList.add(activeClass);
    }

    hideTabContent();
    showTabContent();

    tabsParent.addEventListener('click', function(event) {
        const target = event.target;
        if (target && target.classList.contains(tabsSelector.slice(1))) {
            tabs.forEach((item, i) => {
                if (target == item) {
                    hideTabContent();
                    showTabContent(i);
                }
            });
        }
    });
}

export default tabs;
```

---

## Поддерживаемые особенности

Модуль вкладок поддерживает:

- **Плавное скрытие и отображение контента**: Вкладки плавно появляются и исчезают с использованием классов `show` и `hide`.
- **Установка активной вкладки**: Вкладка, которая активна, получает дополнительный класс для выделения.
- **Обработка кликов на вкладках**: Каждый клик по вкладке активирует соответствующее содержимое и скрывает другие.

---

## Лицензия

Этот проект лицензируется под **MIT License** — вы можете использовать, изменять и распространять его.

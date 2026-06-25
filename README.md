<div align="center">

# ✅ To Do List
### Vanilla JavaScript Todo App

Минималистичное приложение для управления задачами на чистом **Vanilla JavaScript**.  
Полностью адаптивный интерфейс с **БЭМ**-методологией, анимациями и сохранением данных в **localStorage**.

<p>
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black" alt="JavaScript">
</p>

[🔗 **Live Demo**](/) · [🛠 Технологии](#-технологии) · [✨ Возможности](#-ключевые-возможности)

</div>

---

## 🛠 Технологии

| Категория | Стек |
|---|---|
| **Frontend** | HTML5, CSS3, JavaScript (ES6+) |
| **Методологии** | БЭМ, ООП, Component-based Architecture |
| **Шрифты** | Google Fonts (Inter) |

---

## ✨ Ключевые возможности

- ➕ **Добавление задач** — форма с анимированным placeholder (floating label)
- 🔍 **Поиск/фильтрация** — фильтрация по названию задачи
- ✅ **Отметка выполнения** — кастомный чекбокс с зачёркиванием текста
- 🗑 **Удаление задач** — с анимацией исчезновения (opacity + translate)
- 🧹 **Удалить всё** — с подтверждением через `confirm()`
- 💾 **localStorage** — автоматическое сохранение и восстановление задач
- ♿ **Доступность** — `:focus-visible`, ARIA-атрибуты, `pointer-events: none`

---

## 💻 JavaScript Архитектура

### Todo — единый класс с ООП-подходом

```javascript
class Todo {
    selectors = { /* data-js атрибуты */ }
    stateClasses = { isVisible, isDisappearing }
    localStorageKey = 'todo-items'

    constructor() {
        this.state = {
            items: this.getItemsFromLocalStorage(),
            filteredItems: null,
            searchQuery: '',
        }
        this.render()
        this.bindEvents()
    }
}
```

**Особенности реализации:**
- ✅ Централизованное состояние через `this.state`
- ✅ Разделение данных и представления
- ✅ Event delegation на списке задач

### Управление состоянием

```javascript
getItemsFromLocalStorage() {
    const rawData = localStorage.getItem(this.localStorageKey)
    if (!rawData) return []
    try {
        const parsedData = JSON.parse(rawData)
        return Array.isArray(parsedData) ? parsedData : []
    } catch {
        return []
    }
}

saveItemsToLocalStorage() {
    localStorage.setItem(this.localStorageKey, JSON.stringify(this.state.items))
}
```

### Event delegation

```javascript
onClick = ({ target }) => {
    if (target.matches(this.selectors.itemDeleteButton)) {
        const itemElement = target.closest(this.selectors.item)
        itemElement.classList.add(this.stateClasses.isDisappearing)
        setTimeout(() => this.deleteItem(id), 400)
    }
}
```

---

## 🎨 CSS/БЭМ

### Строгая БЭМ-методология

```
.todo                   — блок (корневой контейнер)
.todo__title            — элемент
.todo__form             — элемент
.todo__list             — элемент
.todo-item              — блок (вложенный)
.todo-item__checkbox    — элемент
.todo-item__label       — элемент
.todo-item__delete-button — элемент
.field                  — блок (переиспользуемый)
.button                 — блок (переиспользуемый)
```

**CSS особенности:**
- ✅ CSS Custom Properties — централизованные переменные в `:root`
- ✅ Floating label — через `:has()` и `:placeholder-shown`
- ✅ Кастомный чекбокс — `appearance: none` + SVG иконка
- ✅ Анимация удаления — `is-disappearing` со смещением соседних элементов
- ✅ Touch-friendly — кнопки минимум 44×44px
- ✅ `:focus-visible` — улучшенная доступность

---

## 🏗 Структура проекта

```
src/
├── icons/
│   ├── icon-check_white.svg     # Иконка галочки
│   └── icon-search_black.svg    # Иконка поиска
├── styles/
│   ├── components/
│   │   ├── button.css           # Переиспользуемая кнопка
│   │   ├── field.css            # Поле ввода с floating label
│   │   ├── todo.css             # Основной блок todo
│   │   └── todo-item.css        # Элемент списка задач
│   ├── fonts.css                # Подключение Inter
│   ├── globals.css              # Глобальные стили
│   ├── index.css                # Точка входа (импорты)
│   ├── normalize.css            # Нормализация
│   └── variables.css            # CSS Custom Properties
├── index.html                   # Главная (и единственная) страница
└── script.js                    # Весь JS в одном файле
```

---

## 🚀 Установка и запуск

```bash
# Клонировать репозиторий
git clone https://github.com/qust104/todo-vanilla.git
cd todo-vanilla

# Открыть через локальный сервер (Live Server, http-server или любой другой)
```

---

## 💎 Качество кода

- ✅ Чистая архитектура на Vanilla JavaScript
- ✅ ООП (единый класс `Todo`)
- ✅ Event delegation для списка задач
- ✅ Строгая БЭМ методология
- ✅ CSS Custom Properties для единого стиля
- ✅ Анимации через CSS transitions
- ✅ Сохранение состояния в localStorage
- ✅ ES6+ (Classes, Arrow Functions, template literals, destructuring)
- ✅ Доступность (`:focus-visible`, ARIA label, pointer-events)

---

## 👤 Автор

<div align="center">

🐙 GitHub: [@qust104](https://github.com/qust104)  
📧 Email: az1023415@gmail.com  
💬 Telegram: [@Ninekidoru](https://t.me/Ninekidoru)

</div>

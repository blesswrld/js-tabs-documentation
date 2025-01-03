# JavaScript Tabs Module 🗂️

**JavaScript Tabs Module** provides a component for creating tabs on a web page. This module allows you to easily manage the content of tabs by hiding and showing the corresponding elements when switching between them.

---

## Key Features

1. **Tab Switching**: Easily switch tabs using simple clicks.
2. **Tab Content Animation**: Smoothly add and remove tab content using CSS classes.
3. **Active Tab Setting**: Ability to specify a class for the active tab to highlight it visually.
4. **Click Handling**: Handler for clicks on the parent element of the tabs to switch active tabs.

---

## Installation

1. Clone the repository:
```bash
git clone https://github.com/blesswrld/js-tabs-documentation.git
```

2. Or just download the `tabs.js` file and include it in your project.

---

## Quick Start

### Sample HTML Markup

Make sure your HTML for the tabs has the following structure:

```html
<!-- Tabs Parent Element -->
<div class="tabheader__items">
<div class="tabheader__item">Tab 1</div>
<div class="tabheader__item">Tab 2</div>
<div class="tabheader__item">Tab 3</div>
</div>

<!-- Tab Content -->
<div class="tabcontent">Content for Tab 1</div>
<div class="tabcontent">Content for Tab 2</div>
<div class="tabcontent">Content for Tab 3</div>
```

### Initializing JavaScript

Initialize the tabs by importing the `tabs.js` module and passing in the necessary selectors and active class:

```javascript
import tabs from './modules/tabs.js';

tabs('.tabheader__item', '.tabcontent', '.tabheader__items', 'tabheader__item_active');
```

---

## Usage example

Here's how the tabs module works:

- **Toggle between tabs**: The module allows users to switch between tabs by hiding/showing the corresponding elements.
- **Set active tab**: Specify a class for the active tab to highlight it on the page.
- **Fade content**: Tabs are smoothly shown and hidden using CSS animations.

```javascript
// Main function for switching tabs
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

## Supported Features

The Tabs module supports:

- **Fade in and out of content**: Tabs fade in and out using the `show` and `hide` classes.
- **Set active tab**: The tab that is active gets an additional class for highlighting.
- **Handle clicks on tabs**: Each click on a tab activates the corresponding content and hides the others.

---

## License

This project is licensed under the **MIT License** - you can use, modify and distribute it.

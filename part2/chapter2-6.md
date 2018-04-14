## БЭМ-дерево

Представление структуры веб-страницы в терминах блоков, элементов и модификаторов. Это абстракция над DOM-деревом, которая описывает имена БЭМ-сущностей, их состояния, порядок, вложенность и вспомогательные данные. 

В реальных проектах БЭМ-дерево можно выразить любым форматом, который поддерживает древовидную структуру. 

Рассмотрим пример DOM-дерева: 

```html
<header class="header"> 
  <img class="logo"> 
  <form class="search-form"> 
    <input type="input"> 
    <button type="button"></button> 
  </form>    
  <ul class="lang-switcher">
    <li class="lang-switcher__item"> 
      <a class="lang-switcher__link" href="url">en</a> 
    </li> 
    <li class="lang-switcher__item"> 
      <a class="lang-switcher__link" href="url">ru</a> 
    </li> 
  </ul> 
</header>
```

Ему соответствует такое БЭМ-дерево: 

```
header
  |--logo
  |--search-form
  |   |--input
  |   |--button
  |--lang-switcher
      |--lang-switcher__item
      |   |--lang-switcher__link
      |--lang-switcher__item
          |--lang-switcher__link
```
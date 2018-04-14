## Миксы

Позволяют:

* совмещать поведение и стили нескольких сущностей без дублирования кода;
* одинаково форматировать разные HTML-элементы.

### Внешняя геометрия и позиционирование

В CSS по БЭМ стили, отвечающие за внешнюю геометрию и позиционирование, задаются через родительский блок. 

<strong>Пример</strong> 

HTML-реализация: 

```html
<!-- Блок 'header' --> 
<header class="header"> 
  <button class="button header__button">...</button> 
</header>
```

CSS-реализация кнопки: 

```css
.button { 
  font-family: Arial, sans-serif; 
  text-align: center; 
  border: 1px solid black; /* Рамка */ 
} 
.header__button {   
  margin: 30px; /* Отступ */ 
  position: relative; 
} 
```

В данном примере внешняя геометрия и позиционирование блока `button` задана через элемент `header__button`. Блок `button` не специфицирует никакие отступы и может быть легко переиспользован в любом месте.

HTML-реализация: 

```html
<!-- Блок 'footer' -->
<footer class="footer"> 
  <button class="button">...</button> 
</footer>
```

### Стилизация групп блоков

Иногда необходимо применить одинаковое форматирование сразу к нескольким различным HTML-элементам веб-страницы. Обычно для решения подобных задач применяют групповые селекторы. 

<strong>Пример</strong>

HTML-реализация: 

```html
<article class="article">...</article> 
<footer class="footer"> 
  <div class="copyright">...</div> 
</footer>
```

CSS-реализация: 

```css
article, 
.footer div { 
  font-family: Arial, sans-serif; 
  font-size: 14px; 
  color: #000; 
}
```

В данном примере текст внутри блоков `article` и `copyright` имеет один и тот же цвет и шрифт. 

Несмотря на то, что групповые селекторы позволяют быстро изменить дизайн страницы, такой подход увеличивает связанность кода.

Поэтому в БЭМ для того, чтобы единообразно отформатировать целый набор HTML-элементов, используют миксы. 

<strong>Пример</strong> 

HTML-реализация: 

```html
<article class="article text">...</article> 
<footer class="footer"> 
  <div class="copyright text">...</div> 
</footer>
```

CSS-реализация:

```css
.text { 
  font-family: Arial, sans-serif; 
  font-size: 14px; 
  color: #000; 
}
```
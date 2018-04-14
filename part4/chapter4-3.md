## Модификаторы

Модификаторами в БЭМ задают блокам внешний вид, состояние и поведение. Изменение оформления блока производится при помощи установки/снятия модификатора. 

<strong>Пример</strong> 

HTML-реализация: 

```html
<button class="button button_size_s">...</button>
```

CSS-реализация: 

```css
.button { 
  font-family: Arial, sans-serif; 
  text-align: center; 
} 
.button_size_s { 
  font-size: 13px; 
  line-height: 24px; 
} 
.button_size_m { 
  font-size: 15px;
  line-height: 28px;
}
```

Используя модификаторы, можно изменять представление блока, точечно переопределяя необходимые для этого CSS-свойства. 

Например, так: 

```html
<button class="button button_size_s">...</button> 
<button class="button button_size_m">...</button>
```

Это избавляет от ненужного «Copy-Paste».
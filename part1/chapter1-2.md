## Блок

Функционально независимый компонент страницы, который может быть повторно использован. В HTML блоки представлены атрибутом `class`.

Особенности: 

* Название блока характеризует смысл («что это?» — «меню»: `menu`, «кнопка»: `button`), а не состояние («какой, как выглядит?» — «красный»: `red`, «большой»: `big`).

<strong>Пример</strong>

```html
<!-- Верно. Семантически осмысленный блок 'error' --> 
<div class="error"></div> 

<!-- Неверно. Описывается внешний вид --> 
<div class="red-text"></div>
```

* Блок не должен влиять на свое окружение, т. е. блоку не следует задавать внешнюю геометрию (в виде отступов, границ, влияющих на размеры) и позиционирование. 
* В CSS по БЭМ также не рекомендуется использовать селекторы по тегам или `id`.

Таким образом обеспечивается независимость, при которой возможно повторное использование или перенос блоков с места на место.

### Принцип работы с блоками

#### Вложенность

* Блоки можно вкладывать друг в друга.
* Допустима любая вложенность блоков.

<strong>Пример</strong>

```html
<!-- Блок 'header' --> 
<header class="header"> 
  <!-- Вложенный блок 'logo' --> 
  <div class="logo"></div> 
  <!-- Вложенный блок 'search-form' --> 
  <form class="search-form"></form>
</header>
```
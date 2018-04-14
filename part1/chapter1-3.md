## Элемент

Составная часть блока, которая не может использоваться в отрыве от него. 

Особенности: 

* Название элемента характеризует смысл («что это?» — «пункт»: `item`, «текст»: `text`), а не состояние («какой, как выглядит?» — «красный»: `red`, «большой»: `big`). 
* Структура полного имени элемента соответствует схеме: `имя-блока__имя-элемента`. Имя элемента отделяется от имени блока двумя подчеркиваниями (__).

<strong>Пример</strong>

```html
<!-- Блок 'search-form' --> 
  <form class="search-form"> 
  <!-- Элемент 'input' блока 'search-form' --> 
  <input class="search-form__input"> 
  <!-- Элемент 'button' блока 'search-form' --> 
  <button class="search-form__button">Найти</button> 
</form>
```

### Принципы работы с элементами

* Вложенность
* Принадлежность
* Необязательность

#### Вложенность

* Элементы можно вкладывать друг в друга.
* Допустима любая вложенность элементов.
* Элемент — всегда часть блока, а не другого элемента. Это означает, что в названии элементов нельзя прописывать иерархию вида `block__elem1__elem2`.

<strong>Пример</strong>

```html
<!-- Верно. Структура полного имени элементов соответствует схеме: 'имя-блока__имя-элемента' --> 
<form class="search-form"> 
  <div class="search-form__content"> 
    <input class="search-form__input"> 
    <button class="search-form__button">Найти</button> 
  </div> 
</form> 

<!-- Неверно. Структура полного имени элементов не соответствует схеме: 'имя-блока__имя-элемента' --> 
<form class="search-form"> 
  <div class="search-form__content"> 
    <!-- Рекомендуется: 'search-form__input' или 'search-form__content-input' --> 
    <input class="search-form__content__input"> 
    <!-- Рекомендуется: 'search-form__button' или 'search-form__content-button' --> 
    <button class="search-form__content__button">Найти</button> 
  </div> 
</form>
```

Имя блока задает пространство имен, которое гарантирует зависимость элементов от блока (`block__elem`). 

Блок может иметь вложенную структуру элементов в DOM-дереве: 

<strong>Пример </strong>

```html
<div class="block"> 
  <div class="block__elem1"> 
    <div class="block__elem2"> 
      <div class="block__elem3"></div> 
    </div> 
  </div> 
</div>
```

Однако эта же структура блока в методологии БЭМ всегда будет представлена плоским списком элементов: 

<strong>Пример</strong>

```css
.block {} 
.block__elem1 {} 
.block__elem2 {} 
.block__elem3 {}
```

Это позволяет изменять DOM-структуру блока без внесения правок в коде каждого отдельного элемента: 

<strong>Пример</strong>

```html
<div class="block"> 
  <div class="block__elem1"> 
    <div class="block__elem2"></div> 
  </div> <div class="block__elem3"></div> 
</div>
```

Структура блока меняется, а правила для элементов и их названия остаются прежними.

#### Принадлежность

Элемент — всегда часть блока и не должен использоваться отдельно от него. 

<strong>Пример</strong>

```html
<!-- Верно. Элементы лежат внутри блока 'search-form' --> 
<!-- Блок 'search-form' --> 
<form class="search-form"> 
  <!-- Элемент 'input' блока 'search-form' --> 
  <input class="search-form__input"> 
  <!-- Элемент 'button' блока 'search-form' --> 
  <button class="search-form__button">Найти</button> 
</form> 

<!-- Неверно. Элементы лежат вне контекста блока 'search-form' --> 
<!-- Блок 'search-form' --> 
<form class="search-form"> </form> 

<!-- Элемент 'input' блока 'search-form' --> 
<input class="search-form__input"> 

<!-- Элемент 'button' блока 'search-form' --> 
<button class="search-form__button">Найти</button>
```

#### Необязательность

Элемент — необязательный компонент блока. Не у всех блоков должны быть элементы. 

<strong>Пример</strong>

```html
<!-- Блок 'search-form' --> 
<div class="search-form"> 
  <!-- Блок 'input' --> 
  <input class="input"> 
  <!-- Блок 'button' --> 
  <button class="button">Найти</button>
</div>
```
## Модификатор

Cущность, определяющая внешний вид, состояние или поведение блока либо элемента. Особенности:

* Название модификатора характеризует внешний вид («какой размер?», «какая тема?» и т. п. — «размер»: `size_s`, «тема»: `theme_islands`), состояние («чем отличается от прочих?» — «отключен»: `disabled`, «фокусированный»: `focused`) и поведение («как ведет себя?», «как взаимодействует с пользователем?» — «направление»: `directions_left-top`).
* Имя модификатора отделяется от имени блока или элемента одним подчеркиванием (_).

### Типы модификаторов

#### Булевый

* Используют, когда важно только наличие или отсутствие модификатора, а его значение несущественно. Например, «отключен»: `disabled`. Считается, что при наличии булевого модификатора у сущности его значение равно `true`.
* Структура полного имени модификатора соответствует схеме:
    * `имя-блока_имя-модификатора`; 
    * `имя-блока__имя-элемента_имя-модификатора`.
    
<strong>Пример</strong>

```html
<!-- Блок 'search-form' имеет булевый модификатор 'focused' --> 
<form class="search-form search-form_focused"> 
  <input class="search-form__input"> 
  <!-- Элемент 'button' имеет булевый модификатор 'disabled' --> 
  <button class="search-form__button search-form__button_disabled">Найти</button> 
</form>
```

#### Ключ-значение

* Используют, когда важно значение модификатора. Например, «меню с темой оформления `islands`»: `menu_theme_islands`.
* Структура полного имени модификатора соответствует схеме:
    * `имя-блока_имя-модификатора_значение-модификатора`; 
    * `имя-блока__имя-элемента_имя-модификатора_значение-модификатора`.
    
<strong>Пример</strong>

```html
<!-- Блок 'search-form' имеет модификатор 'theme' со значением 'islands' --> 
<form class="search-form search-form_theme_islands">
  <input class="search-form__input"> 
  <!-- Элемент 'button' имеет модификатор 'size' со значением 'm' --> 
  <button class="search-form__button search-form__button_size_m">Найти</button> 
</form> 

<!-- Невозможно одновременно использовать два одинаковых модификатора с разными значениями --> 
<form class="search-form search-form_theme_islands search-form_theme_lite"> 
  <input class="search-form__input"> 
  <button class="search-form__button search-form__button_size_s search-form__button_size_m"> Найти </button> 
</form>
```

### Принципы работы с модификаторами

#### Модификатор нельзя использовать самостоятельно

С точки зрения БЭМ-методологии модификатор не может использоваться в отрыве от модифицируемого блока или элемента. Модификатор должен изменять вид, поведение или состояние сущности, а не заменять ее. 

<strong>Пример</strong>

```html
<!-- Верно. Блок 'search-form' имеет модификатр 'theme' со значением 'islands'--> 
<form class="search-form search-form_theme_islands"> 
  <input class="search-form__input"> 
  <button class="search-form__button">Найти</button> 
</form> 

<!-- Неверно. Отсутствует модифицируемый класс 'search-form' --> 
<form class="search-form_theme_islands"> 
  <input class="search-form__input"> 
  <button class="search-form__button">Найти</button> 
</form>
```
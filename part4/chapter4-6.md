## Работа с уровнями переопределения

Применение принципов БЭМ-методологии к CSS позволяет разделять представление блоков по разным уровням. 

Разделение по уровням позволяет:

* реализовывать новый внешний вид блока на другом уровне переопределения, сохраняя предыдущий, наследовать и дополнять его;
* полностью перекрывать внешний вид блока (переопределять);
* добавлять блоки с новым представлением.

С помощью уровней переопределения можно создать универсальную CSS-библиотеку блоков и изменять ее на проектном уровне. Затем использовать сборку и включать в проект только необходимое представление блоков.

<strong>Пример</strong> 

```
common.blocks/ 
    button/ 
        button.css # Базовая CSS-реализация кнопки 

desktop.blocks/ 
    button/ 
        button.css # Особенности кнопки для desktop 
        
mobile.blocks/ 
    button/ button.css # Особенности кнопки для mobile 
```
   
При сборке в файл `desktop.css` попадут все базовые CSS-правила кнопки с уровня common и переопределенные правила с уровня `desktop`. 

```css
@import "common.blocks/button/button.css";  /* Базовые CSS-правила */ 
@import "desktop.blocks/button/button.css"; /* Особенности desktop */ 
```

Файл `mobile.css` будет включать базовые CSS-правила кнопки с уровня `common` и переопределенные правила с уровня `mobile`. 

```css
@import "common.blocks/button/button.css"; /* Базовые CSS-правила */ 
@import "mobile.blocks/button/button.css"; /* Особенности mobile */ 
```

Разделение представления блока button по разным уровням позволяет:

* Полностью перекрыть внешний вид блока на другом уровне переопределения. 
`common.blocks/button/button.css`

```css
.button { 
  font-family: Arial, sans-serif; 
  font-size: 11px; 
  line-height: 24px; 
  background: #fff; 
} 
```

`desktop.blocks/button/button.css` 

```css
.button { 
  font-family: 'Roboto', sans-serif; 
  font-size: 13px; 
  line-height: 28px; 
  background: yellow; 
}
```

* Добавить или частично изменить внешний вид блока на другом уровне переопределения. 
`common.blocks/button/button.css`

```css
.button { 
  font-family: Arial, sans-serif; 
  font-size: 11px; 
  line-height: 24px; 
  background: #fff; 
} 
```

`desktop.blocks/button/button.css` 

```css
.button { 
  background: #fff; 
  color: rgb(255, 0, 0); 
  box-shadow: 0 0 10px rgba(0,0,0,0.5); 
}
```
# Описание

Данное расширение позволяет работать с data-атрибутами элементов также, как с классами.

# Основные команды

## .addData(name, value)

Дабавляет элементам в атрибут *data-name* значение *value*. Команда защищена от дублирования.

### Пример:

Элемент
```html
<div id="element"></div>
```

Команда
```js
jQuery('#element').addData('text-format', 'bold');
```
Результат
```html
<div id="element" data-text-format="bold"></div>
```

Команда 
```js
jQuery('#element').addData('text-format', 'italic');
```
Результат
```html
<div id="element" data-text-format="bold italic"></div>
```

Команда
```js
jQuery('#element').addData('text-format', 'bold');
```
Результат
```html
<div id="element" data-text-format="bold italic"></div>
<!-- 'bold' в data-text-format уже есть, ничего не произойдет -->
```

Команда
```js
jQuery('#element').addData('status', 'active');
```
Результат
```html
<div id="element" data-text-format="bold italic" data-status="active"></div>
```

## .eraseData(name, value)[^1]

Удаляет элементам из атрибута *data-name* значение *value*. Если *value* в *data-name* нет, ничего не произойдет.

### Пример:

Элемент
```html
<div id="element" data-text-format="bold italic"></div>
```

Команда
```js
jQuery('#element').eraseData('text-format', 'bold');
```
Результат
```html
<div id="element" data-text-format="italic"></div>
```

Команда
```js
jQuery('#element').eraseData('text-format', 'through');
```
Результат
```html
<div id="element" data-text-format="italic"></div>
<!--'through' в data-text-format нет, ничего не произойдет-->
```

Команда
```js
jQuery('#element').eraseData('text-format', 'italic');
```
Результат
```html
<div id="element"></div>
```

## .toggleData(name, value)

Создает элементам в атрибут *data-name* значение *value*, если его нет, или удаляет элементам из атрибута *data-name* значение *value*, если он есть.

### Пример:

Элемент
```html
<div id="element"></div>
```

Команда
```js
jQuery('#element').toggleData('text-format', 'bold');
```
Результат
```html
<div id="element" data-text-format="bold"></div>
```

Команда
```js
jQuery('#element').toggleData('text-format', 'italic');
```
Результат
```html
<div id="element" data-text-format="bold italic"></div>
```

Команда
```js
jQuery('#element').toggleData('text-format', 'through');
```
Результат
```html
<div id="element" data-text-format="bold italic through"></div>
```

Команда
```js
jQuery('#element').toggleData('text-format', 'italic');
```
Результат
```html
<div id="element" data-text-format="bold through"></div>
```

## .hasData(name, value)

Проверяет в элементах наличие значения *value* у атрибута *data-name*. Возвращает `true` или `false`.

### Пример:

Элемент
```html
<div id="element" data-text-format="bold italic"></div>
```

Команда
```js
jQuery('#element').hasData('text-format', 'bold'); // true
```
Команда
```js
jQuery('#element').hasData('text-format', 'italic'); // true
```
Команда
```js
jQuery('#element').hasData('text-format', 'through'); // false
```

# Примечания

* *value* может принимать несколько значений, разделенных пробелом. В этом случае каждое значение обработается отдельно, а в команде **.hasData()** проверка выполнится на наличие всех указанных значений и вернёт `true`, если все указанные значения присутствуют.
* Если в *value* передать что-то отличное от строки, это будет эквивалентно передаче пустой строки. Для **.addData()**, **.eraseData()** и **.toggleData()** ничего не произойдет, а **.hasData()** вернет `true`.

[^1]: Команда **.removeData()** уже используется в jQuery, поэтому сделал **.eraseData()**

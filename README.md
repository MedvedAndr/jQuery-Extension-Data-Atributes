# Описание

Данное расширение позволяет работать с data-атрибутами элементов также, как с классами

# Основные команды

## .addData(name, value)

Дабавляет элементам в атрибут data-name значение value. Команда защищена от дублирования.

### Пример:

Элемент `<div id="element"></div>`

Команда `jQuery('#element').addData('text-format', 'bold');`<br>
Результат `<div id="element" data-text-format="bold"></div>`

Команда `jQuery('#element').addData('text-format', 'italic');`<br>
Результат `<div id="element" data-text-format="bold italic"></div>`

Команда `jQuery('#element').addData('text-format', 'bold');`<br>
Результат `<div id="element" data-text-format="bold italic"></div> // 'bold' в data-text-format уже есть, ничего не произойдет`

Команда `jQuery('#element').addData('status', 'active');`<br>
Результат `<div id="element" data-text-format="bold italic" data-status="active"></div>`

## .eraseData(name, value)*

Удаляет элементам из атрибута data-name значение value. Если value в data-name нет, ничего не произойдет.

\* команда **.removeData()** уже используется в jQuery, поэтому сделал **.eraseData()**

### Пример:

Элемент `<div id="element" data-text-format="bold italic"></div>`

Команда `jQuery('#element').eraseData('text-format', 'bold')`<br>
Результат `<div id="element" data-text-format="italic"></div>`

Команда `jQuery('#element').eraseData('text-format', 'through')`<br>
Результат `<div id="element" data-text-format="italic"></div> // 'through' в data-text-format нет, ничего не произойдет`

Команда `jQuery('#element').eraseData('text-format', 'italic')`<br>
Результат `<div id="element"></div>`

## .toggleData(name, value)

Создает элементам в атрибут data-name значение value, если его нет, или удаляет элементам из атрибута data-name значение value, если он есть.

### Пример:

Элемент `<div id="element"></div>`

Команда `jQuery('#element').toggleData('text-format', 'bold')`<br>
Результат `<div id="element" data-text-format="bold"></div>`

Команда `jQuery('#element').toggleData('text-format', 'italic')`<br>
Результат `<div id="element" data-text-format="bold italic"></div>`

Команда `jQuery('#element').toggleData('text-format', 'through')`<br>
Результат `<div id="element" data-text-format="bold italic through"></div>`

Команда `jQuery('#element').toggleData('text-format', 'italic')`<br>
Результат `<div id="element" data-text-format="bold through"></div>`

## .hasData(name, value)

Проверяет в элементах наличие значения value у атрибута data-name. Возвращает true или false.

### Пример:

Элемент `<div id="element" data-text-format="bold italic"></div>`

Команда `jQuery('#element').hasData('text-format', 'bold') // true`<br>
Команда `jQuery('#element').hasData('text-format', 'italic') // true`<br>
Команда `jQuery('#element').hasData('text-format', 'through') // false`<br>

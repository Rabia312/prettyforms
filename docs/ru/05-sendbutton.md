---
currentMenu: sendbutton
---

## Атрибуты кнопки отправки формы

Кнопка, нажатие на которую генерирует отправку формы, может также иметь несколько дополнительных атрибутов, объясняющих,
куда должны быть отправлены данные, из какого DOM-элемента они должны быть собраны, и некоторые
другие свойства поведения формы. Если атрибуты не были указаны, данные будут взяты из вашей формы.

| атрибут       | Описание | Обязательно? |
| ------------- | ---------|--------------|
| data-input  | jQuery-селектор элемента, из которого будут собраны данные для отправки на сервер  | Нет, если не указано, то будет сделана попытка вытащить данные из формы, в которой лежит кнопка. Если формы не было найдено, будет отправлен запрос без данных. |
| href или data-link  | Адрес, на который будут отправлены данные  | Нет, по умолчанию данные будут взяты из атрибута action формы, если же и там пусто, то они будут отправлены на текущий URL страницы |
| data-clearinputs="true" | Очистить поля формы после успешного выполнения запроса?  | Нет |
| class="... really"  | Позволяет задать вопрос перед отправкой данных. Если к сайту подключён плагин [SweetAlert](https://github.com/t4t5/sweetalert), он будет задействован. | Нет |
| data-really-text=""  | Текст вопроса, по умолчанию берется из `PrettyForms.messages.really` | Нет |
| data-really-text-btn=""  | Текст кнопки, нажатие на которую вызовет выполнение действия. По-умолчанию, текст берется из `PrettyForms.messages.really_agree` | Нет |
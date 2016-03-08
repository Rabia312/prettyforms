---
currentMenu: serverside
---

## Формат протокола общения клиента с сервером

Клиентская библиотека ожидает от сервера ответ в следующем формате:
```javascript
{
  command_name_1 : "params",
  command_name_2 : "params"
}
```

Для отображения ошибок валидации, необходимо послать клиенту следующий ответ:
```javascript
{
  validation_errors: {
    form_field_1: ["текст ошибки №1", "текст ошибки №2"],
    form_field_2: ["текст ошибки №1", "текст ошибки №2", "текст ошибки №2"]
  }
}
```

## Обработка команд с сервера на клиенте

Изначально библиотека поддерживает следующие команды, которые можно отправлять ей с сервера:

| команда       | Описание | Параметры |
| ------------- | ---------|--------------|
| `validation_errors`  | Вывести ошибки валидации  | Объект, где ключи - названия полей, значения - массивы с ошибками. Либо просто строка, тогда она будет выведена рядом с кнопкной отправки формы  |
| `redirect`  | Произвести редирект пользователя на другую страницу  | URL страницы |
| `refresh` | Обновить текущую страницу  | Нет |
| `nothing`  | Ничего не делать | Нет |
| `success`  | Вывести сообщение об успехе | `{ title: 'Заголовок', text: 'Текст сообщения'  }` |
| `warning`  | Вывести сообщение об опасности | `{ title: 'Заголовок', text: 'Текст сообщения'  }` |
| `info`  | Вывести информативное сообщение | `{ title: 'Заголовок', text: 'Текст сообщения'  }` |
| `error`  | Вывести сообщение об ошибке | `{ title: 'Заголовок', text: 'Текст сообщения'  }` |

Для команд `success`, `warning`, `info` и `error` действительно следующее: если к вашему сайту будет подключён плагин [SweetAlert](https://github.com/t4t5/sweetalert), то он будет задействован при их выполнении.

## Собственные команды

Вы можете легко добавить свои собственные команды, чтобы выполнять
их в браузере тогда, когда сервер вернёт ваш команду.

Пример добавления собственного обработчика события:
```javascript
PrettyForms.Commands.registerHandler('command_name', function (data) {
  // делаем здесь всё, что хочем.
  // data - это объект с данными, которые отправил нам сервер
});
```
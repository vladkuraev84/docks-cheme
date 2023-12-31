# Menu

> Размещен в `modules`.

Модуль **"Меню"** предоставляет возможность настройки и отображения навигационного меню в вашем приложении. Этот модуль позволяет добавлять и настраивать пункты меню, которые могут быть связаны с различными страницами или действиями в вашем приложении.

### Конфигурация модуля

Модуль **"Меню"** настраивается с использованием JSON-объекта. Пример конфигурации модуля с пояснениями приведен ниже:

```json
{
  "config": {
    "modules": [
      {
        "name": "menu",
        "enable": true,
        "config": {
          "list": [
            {
              "id": 1,
              "pageId": 1,
              "position": 1,
              "enable": true,
              "title": "menu.title"
            },
            {
              "id": 2,
              "pageId": 3,
              "position": 3,
              "enable": true,
              "title": "#Текст тайтл"
            }
          ]
        }
      }
    ]
  }
}
```

### Настройка модуля "Меню"

Модуль **"Меню"** имеет следующие свойства внутри своего объекта конфигурации:

- **"name"**: Название модуля. Должно быть установлено как `"menu"`.
- **"enable"**: Определяет, включен ли модуль. Установите `"true"`, чтобы включить модуль **"Меню"**.
- **"config"**: Объект настройки для модуля **"Меню"**.

### Параметры пунктов меню

Внутри объекта `config` модуля **"Меню"** определен массив **list**, который содержит параметры для каждого пункта меню:

- **"id"**: Уникальный идентификатор пункта меню.
- **"pageId"**: Идентификатор страницы или действия, с которым связан данный пункт меню.
- **"position"**: Позиция пункта меню в списке. Чем меньше значение, тем выше будет пункт.
- **"enable"**: Определяет, активен ли пункт меню. Установите `"true"`, чтобы пункт был активен.
- **"title"**: Текст заголовка пункта меню. Может быть строкой или ссылкой на ключ локализации.

Модуль **"Меню"** предоставляет гибкую настройку и отображение навигационного меню в вашем приложении. Путем настройки массива list вы можете добавлять, изменять и управлять страницами(пунктами) меню, обеспечивая эффективную навигацию для пользователей.
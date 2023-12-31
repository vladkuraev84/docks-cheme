# Схема вида

### Общая структура схемы:

Структура схемы формы состоит из двух ключевых частей: **config** и **pages**. Эта схема предоставляет гибкую и настраиваемую основу для создания индивидуальных форм сбора данных. Давайте рассмотрим каждую часть более подробно.

### Часть 1: `config`

`config` содержит общие настройки и параметры формы:

[//]: # (- **step_by_step**: Опциональный параметр для указания процесса заполнения формы пошагово. Здесь можно описать этапы заполнения формы.)
- **modules**: Массив модулей, которые можно использовать в форме. Модули предоставляют дополнительные функциональные возможности для формы.
- **apiBaseUrl**: Базовый URL для взаимодействия с внешними сервисами через API.
- **localization**: Объект для локализации текстовых элементов формы на различных языках.
- **styles**: Массив стилей, которые могут быть применены к форме. Здесь можно указать различные варианты оформления.
- **variables**: Переменные, которые можно использовать в различных частях формы. Например, **selectorCountryList** может быть объектом со списком стран для выбора.

### Часть 2: `pages`

`pages` содержит описание отдельных страниц формы:

- **id**: Уникальный идентификатор страницы.
- **key**: Ключ страницы, который может использоваться для идентификации страницы в коде.
- **description**: Описание страницы, которое может пояснить её назначение или содержание. Он же название страницы.
- **components**: Массив компонентов, которые составляют содержимое страницы. Компоненты могут быть полями ввода, кнопками и другими элементами.

Для формирования блока компонентов используется стандартная структура, которая используется в `json`, а именно: `{}`, - фигурные скобочки обозначают, что в данном блоке будет формироваться блок компонентов. В дальнейшем на всех примерах вы увидите все блоки, помещенные в `{}`.

```json
{
	"config": {
		"modules": [{}],
		"apiBaseUrl": "",
		"localization": {},
		"styles": {
			"value": ["form-widget-g p { margin-bottom: 20px; }", ... ]
		},
		"variables": {
			"selectorCountryList": {
              "AL": "#Alabama",
              "AK": "#Alaska",
              "AZ": "#Arizona"
            }
		}
	},
	"pages": [
		{
			"id": 1,
			"key": "personal-info",
			"description": "User's personal information",
			"components": [
              {
                "common": {
                  "type": "TextContainer",
                  "class": {
                    "container": "text-center"
                  }
                },
                "custom": {
                  "tag": "h2"
                },
                "text": {
                  "value": "Application text"
                }
              },
              ...
            ]
		}
	]
}
```

Эта документация поможет вам более глубоко понять структуру и параметры схемы формы, что обеспечит более эффективное создание и настройку индивидуальных форм сбора данных в рамках вашего проекта.
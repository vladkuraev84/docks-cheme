# JSONS. Элементы страницы

> Наглядный пример как определять и настраивать различные компоненты, которые будут отображаться на странице вашего приложения. Пример показывает гибкость в создании макетов и внешнего вида страницы с помощью настройки компонентов.

### Конфигурация элементов страницы

Конфигурация элементов страницы определяется с использованием JSON-объекта. Пример конфигурации элементов страницы с пояснениями приведен ниже:

```json
{
  "pages": [
    {
      "id": 1,
      "key": "welcome",
      "description": "Welcome",
      "components": [
        {
          "common": {
            "type": "TextContainer",
            "class": {
              "container": "--center"
            }
          },
          "custom": {
            "tag": "h2"
          },
          "text": {
            "value": "Пример текста"
          }
        },
        {
          // ... Другие компоненты ...
        }
      ]
    }
  ]
}

```

### Описание элементов страницы

Каждый элемент страницы имеет следующие свойства внутри массива `"components"` (аттрибуты списка снизу будут повторяться в соответствующих разделах):

- **"common"**: Общие параметры компонента.
  - **"type"**: Тип компонента, определяющий его поведение и отображение.
  - **"class"**: CSS-классы, применяемые к контейнеру компонента.
- **"custom"**: Пользовательские параметры компонента, зависящие от типа компонента.
- **"validation"**: Параметры валидации компонента.
  - **"required"**: Определяет, является ли компонент обязательным для заполнения.
  - **"pattern"**: Регулярное выражение для дополнительной валидации значения.
  - **"texts"**: Тексты для сообщений об ошибках валидации.
- **"text"**: Текстовые параметры компонента.
  - **"placeholder"**: Плейсхолдер (подсказка) для ввода текста.
  - **"label"**: Текст метки (названия) компонента.

### Пример использования элементов страницы

Пример ниже демонстрирует конфигурацию различных компонентов на странице "Welcome":

```json
{
  "pages": [
    {
      "id": 1,
      "key": "welcome",
      "description": "Welcome",
      "components": [
        {
          "common": {
            "type": "TextContainer",
            "class": {
              "container": "--center" // размещение по центру
            }
          },
          "custom": {
            "tag": "h2"
          },
          "text": {
            "value": "text example"
          }
        },
        {
          "common": {
            "type": "InputEmail",
            "model": "email",
            "enable": true
          },
          "validation": {
            "required": true,
            "pattern": "/^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+.[a-zA-Z0-9-.]+$/",
            "texts": {
              "required": "#Обязательное поле",
              "pattern": "#Введите валидный адресс почты"
            }
          },
          "text": {
            "placeholder": "#name@company.com",
            "label": "#E-mail"
          }
        },
        {
          "common": {
            "type": "LayoutContainer",
            "class": {
              "container": "my-class"
            },
            "enable": true
          },
          "components": [
            {
              "common": {
                "type": "LayoutContainer",
                "class": {
                  "container": "g-12-cols"
                }
              },
              "components": [
                {
                  "common": {
                    "type": "InputText",
                    "model": "firstName"
                  },
                  "custom": {
                    "pattern": "/^[a-zа-я_ ]{0,28}$/i"
                  },
                  "validation": {
                    "required": true,
                    "texts": {
                      "required": "#Обязательное поле"
                    }
                  },
                  "text": {
                    "label": "#Имя"
                  }
                }
              ]
            }
          ]
        },
        {
          "common": {
            "type": "LayoutContainer",
            "class": {
              "container": "g-2-cols"
            }
          },
          "components": [
            {
              "common": {
                "type": "InputText",
                "model": "cellPhoneNumber"
              },
              "custom": {
                "mask": "(###) ###-####"
              },
              "validation": {
                "required": true,
                "pattern": "/^\\(\\d{3}\\) \\d{3}-\\d{4}$/",
                "texts": {
                  "required": "#Обязательное поле",
                  "pattern": "#Введите валидный номер телефона"
                }
              },
              "text": {
                "placeholder": "#(555) 555-5555",
                "label": "#Номер телефона"
              }
            },
            {
              "common": {
                "type": "InputDate",
                "model": "birthDate",
                "enable": true
              },
              "custom": {
                "mask": "##/##/####",
                "hint": "#format: mm/dd/yyyy"
              },
              "module": {
                "minDate": "01/01/1920",
                "maxDate": "01/01/2005"
              },
              "validation": {
                "required": true,
                "texts": {
                  "required": "#Обязательное поле",
                  "range": "#Дата за пределами диапозон от 01/01/1920 до 01/01/2005",
                  "notValid": "#Это невалидная дата."
                }
              },
              "text": {
                "placeholder": "#example: 01/25/1963",
                "label": "#Date of birth"
              }
            }
          ]
        },
        {
          "common": {
            "type": "LayoutContainer",
            "enable": true,
            "class": {
              "container": "g-3-cols"
            }
          },
          "components": [
            {
              "common": {
                "type": "Selector",
                "model": "state"
              },
              "custom": {
                "options": "$:selectorCountryList",
                "defaultText": "#Выберите штат"
              },
              "validation": {
                "required": true,
                "texts": {
                  "required": "#Обязательное поле"
                }
              },
              "text": {
                "label": "#Штат *"
              }
            },
            {
              "common": {
                "type": "InputText",
                "model": "zipCode"
              },
              "custom": {
                "pattern": "/^.{0,35}$/i"
              },
              "validation": {
                "required": true,
                "texts": {
                  "required": "#Обязательное поле"
                }
              },
              "text": {
                "placeholder": "",
                "label": "#Индекс"
              }
            }
          ]
        },
        {
          "common": {
            "type": "LayoutContainer",
            "class": {
              "container": "col-7 col-9-sm --col-middle"
            }
          },
          "components": [
            {
              "common": {
                "type": "Radiobuttons",
                "model": "cdlHolder",
                "class": {
                  "container": "--radio-space-evenly"
                }
              },
              "custom": {
                "options": [
                  {
                    "value": "yes",
                    "text": "#Yes",
                    "action": {
                      "type": "SHOW_CONTAINER",
                      "nextSibling": 1
                    }
                  },
                  {
                    "value": "no",
                    "text": "#No",
                    "action": {
                      "type": "HIDE_CONTAINER",
                      "nextSibling": 1
                    }
                  }
                ]
              },
              "text": {
                "label": "#Просто пример тайтла"
              },
              "validation": {
                "required": true
              }
            },
            {
              "common": {
                "type": "Selector",
                "model": "cdlExperience"
              },
              "attrs": {
                "container": {
                  "hidden": true
                },
                "component": {}
              },
              "custom": {
                "options": {
                  "LessThan3Months": "#Может быть ваш ключ 1",
                  "_4To6Months": "#Может быть ваш ключ 2",
                  "MoreThan6Months": "#Может быть ваш ключ 3"
                },
                "defaultText": "#Выберите вариант"
              },
              "validation": {
                "required": true,
                "requiredOnlyIfVisible": true,
                "texts": {
                  "required": "#Обязательное поле"
                }
              },
              "text": {
                "label": "#Пример *"
              }
            },
            {
              "common": {
                "type": "Radiobuttons",
                "model": "drugTest",
                "class": {
                  "container": "--radio-space-evenly"
                }
              },
              "custom": {
                "options": [
                  {
                    "value": "yes",
                    "text": "#Да"
                  },
                  {
                    "value": "no",
                    "text": "#Нет"
                  }
                ]
              },
              "text": {
                "label": "#Можете выбрать?"
              },
              "validation": {
                "required": true
              }
            },
            {
              "common": {
                "type": "Checkbox",
                "model": "agree"
              },
              "custom": {
                "bodyHTML": "#Согласен с <a href='/job_application#terms' target='_blank'>правилами.</a>"
              },
              "validation": {
                "required": true
              }
            }
          ]
        },
        {
          "common": {
            "type": "ButtonSubmit",
            "class": {
              "container": "col-5 col-5-sm --col-middle"
            }
          },
          "custom": {},
          "text": {
            "text": "#Сохранить"
          }
        }
      ]
    }
  ]
}
```

Проект предоставляет мощный инструмент для создания разнообразных компонентов на страницах вашего приложения. Путем настройки каждого компонента вы можете создавать интерактивные и информативные интерфейсы, которые соответствуют потребностям пользователей.
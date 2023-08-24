# Layouts

> Раздел для организации компонентов формы

Данный раздел описывает структуру и параметры, необходимые для эффективной организации элементов формы в блоках, используя ключевые понятия `"common"`, `"type"`, `"class"` `"model"`и `"enable"`.

### Параметры Блока `"common"`:

- **"type"**: Определяет тип блока. Допустимые значения: **"LayoutContainer"** (контейнер макета) или **"LayoutColumns"** (двухколоночный макет), а так же данный атрибут используется для определения типа компонента:  [InputText, InputPassword, InputEmail, InputDate, Selector, Textarea, Radiobuttons, Checkbox].
- **"class"**: Опционально. Позволяет присвоить блоку дополнительный CSS-класс для стилизации. Пример значения: `"standard-radio"`. Релевантные значения: [LayoutColumns, LayoutColumn, LayoutContainer, MultiBox, InputText, InputPassword, InputEmail, InputDate, Selector, Textarea, Radiobuttons, Checkbox].
  - **"container"**: Применяется ко всем элементам. Указывает класс контейнера для стилизации. Пример значения: `"container class"`.
  - **"element"**: Применяется к инпутам и единичным контейнерам. Указывает класс для стилизации внутренних элементов. Пример значения: `"input class name"` - Имеется у всех инпутов, и у единичных контейнеров (так как не у всех есть возможность логически иметь такой внутренний div)
- **"model"**: Опционально. Указывает модель данных, связанную с компонентами внутри блока. Пример: `"cdlHolder"`.  Релевантные значения: [InputText, InputPassword, InputEmail, InputDate, Selector, Textarea, Radiobuttons, Checkbox].
- **"enable"**: Опционально. Если установлено значение `"true"`, компоненты внутри блока будут полностью включены в форму. Это может быть использовано для фильтрации на клиентской стороне.

### Пример:

```json
{
  "common": {
    "type": "LayoutContainer",
    "class": {
      "container": "my-class-name"
    },
    "enable": true
  },
  "components": [
    {
      "common": {
        "type": "TextContainer",
        "class": {
          "container": "my-class-name-for-this-block"
        },
        ...
      }
    },

    {
      "common": {
        "type": "LayoutContainer",
        "class": {
          "container": "g-2-cols" // класс сетки означает, что два блока в массиве "components" будут разбиты на две колонки
        },
        ...
      },
      "components": [
        {
          "common": {
            "type": "InputText",
            "model": "firstName"
          },
          ...
        },
        {
          "common": {
            "type": "InputText",
            "model": "lastName"
          },
          ...
        }
      ]
    }
  ]
}
```

В проекте разработаны две схемы организации компонентов формы: `"LayoutContainer"` и `"LayoutColumns"`. Данные `"type"` показывают, как эффективно располагать элементы формы в блоках с разной структурой. Вы можете выбрать подходящий тип блока в зависимости от требований вашего проекта. Как минимум один из этих ключей должен присутствовать при сборке блока компонентов(а). 

В блоке `"LayoutContainer"`, как видно из примера выше, возможно дополнительное присвоение класса, а так же класса для управления сеткой (**".col-1"** - **".col-12"**). 

`"LayoutColumns"` имеет строгую двухколоночную схему размещения элементов формы. Как видно в примере `"type": "LayoutColumns"` говорит нам о том, что внутри будет находится один или два `"components"` с `"type": "LayoutColumn"`. Каждый `"LayoutColumn"` имеет класс `".col-6"` и согласно 12-колоночной схемы разделение по горизонтале данный класс показывает, что блок будет занимать половину горизонтальной ширины блока.

### Пример:

```json
{
    "common": {
        "type": "LayoutColumns"
    },
    "components": [
        {
            "common": {
                "type": "LayoutColumn"
            },
            "components": [
                {
                    "common": {
                        "type": "InputText",
                        "model": "myModel"
                    }
                }
            ]
        },
        {
            "common": {
                "type": "LayoutColumn"
            },
            "components": [
                {
                    "common": {
                        "type": "InputText_2",
                        "model": "myModel_2"
                    }
                }
            ]
        }
    ]
}
```


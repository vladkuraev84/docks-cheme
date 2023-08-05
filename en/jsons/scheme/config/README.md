# JSONS. Конфиг

Вид конфига:

```
{
	"config": {
		"step_by_step": "strict",
		"modules": [
		    {
				"name": "datepicker",
				"enable": true,
				"config": {
					"locales": {
						"relations": {
							"ua": "uk",
							"fr": "fr"
						}
					},
					"forEachField": {
						"format": "mm/dd/yyyy",
						"autohide": true,
						"todayHighlight": true
					}
				}
			},
			....
		],
		"apiBaseUrl": "http://localhost:8081/api/",
		"localization": {
			"defaultLang": "en",
			"availableLangs": ["en", "fr", "ua", "ru"]
		},
		"styles": {
			"value": [
				"form-widget-g .fieldset-title p { margin-bottom: 20px; }",
				....
			]
		},
		"variables": {
			"selectorCountryList": {
				"AL": "#Alabama",
				....
			}
		}
	},
```

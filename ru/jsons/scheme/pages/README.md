# JSONS. Элементы страницы

> Включает в себя ряд элементов, которые описаны в данном разделе.

Вид элементов для страниц:

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
						"value": "driver application"
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
							"required": "errors.required",
							"pattern": "#Please enter a valid email address"
						}
					},
					"text": {
						"placeholder": "#name@company.com",
						"label": "#E-mail address"
					}
				},
				{
					"common": {
						"type": "LayoutContainer",
						"class": {
							"container": "bordered-block"
						},
						"enable": true
					},
					"components": [
						{
							"common": {
								"type": "TextContainer",
								"class": {
									"container": "fieldset-title"
								}
							},
							"custom": {
								"tag": "p"
							},
							"text": {
								"value": "#Full legal name (as it appears on your driver's license)"
							},
							"styles": {
								"value": ""
							}
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
										"model": "firstName"
									},
									"custom": {
										"pattern": "/^[a-zа-я_ ]{0,28}$/i"
									},
									"validation": {
										"required": true,
										"texts": {
											"required": "errors.required"
										}
									},
									"text": {
										"label": "#First name"
									}
								},
								{
									"common": {
										"type": "InputText",
										"model": "lastName"
									},
									"custom": {
										"pattern": "/^[a-zа-я_ ]{0,28}$/i"
									},
									"validation": {
										"required": true,
										"texts": {
											"required": "errors.required"
										}
									},
									"text": {
										"label": "#Last name"
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
									"required": "errors.required",
									"pattern": "#Please enter a valid phone number"
								}
							},
							"text": {
								"placeholder": "#(555) 555-5555",
								"label": "#Cell phone number"
							}
						},
						{
							"common": {
								"type": "InputText",
								"model": "homePhoneNumber"
							},
							"custom": {
								"mask": "(###) ###-####"
							},
							"text": {
								"placeholder": "#(555) 555-5555",
								"label": "#Home phone number"
							}
						},
						{
							"common": {
								"type": "InputText",
								"model": "streetAddress"
							},
							"custom": {
								"pattern": "/^.{0,40}$/i"
							},
							"validation": {
								"required": true,
								"texts": {
									"required": "errors.required"
								}
							},
							"text": {
								"placeholder": "#P.O. box, company name",
								"label": "#Street address"
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
									"required": "errors.required",
									"range": "#The date falls outside of the acceptable range. From 01/01/1920 to 01/01/2005",
									"notValid": "#This is not a valid date."
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
								"type": "InputText",
								"model": "city"
							},
							"custom": {
								"pattern": "/^.{0,40}$/i"
							},
							"validation": {
								"required": true,
								"texts": {
									"required": "errors.required"
								}
							},
							"text": {
								"label": "#City"
							}
						},
						{
							"common": {
								"type": "Selector",
								"model": "state"
							},
							"custom": {
								"options": "$:selectorCountryList",
								"defaultText": "#Select Your state"
							},
							"validation": {
								"required": true,
								"texts": {
									"required": "errors.required"
								}
							},
							"text": {
								"label": "#State *"
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
									"required": "errors.required"
								}
							},
							"text": {
								"placeholder": "",
								"label": "#Zip code"
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
								"label": "#Do you have a commercial driver's license? (class A)"
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
									"LessThan3Months": "#Less than 3 months",
									"_4To6Months": "#4 to 6 months",
									"MoreThan6Months": "#More than 6 months "
								},
								"defaultText": "#Select Your CDL experience"
							},
							"validation": {
								"required": true,
								"requiredOnlyIfVisible": true,
								"texts": {
									"required": "errors.required"
								}
							},
							"text": {
								"label": "#CDL experience *"
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
										"text": "#Yes"
									},
									{
										"value": "no",
										"text": "#No"
									}
								]
							},
							"text": {
								"label": "#Can you pass a drug test?"
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
								"bodyHTML": "#I have read and agreed with <a href='/job_application#terms' target='_blank'>the terms and conditions.</a>"
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
						"text": "#Submit"
					}
				}
			]
		},
	]
```

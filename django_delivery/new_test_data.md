// firstname: Это поле не может быть пустым.
{"products": [{"product": 1, "quantity": 1}], "firstname": null, "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

// Ключей заказа вообще нет.
// firstname, lastname, phonenumber, address: Обязательное поле.
{"products": [{"product": 1, "quantity": 1}]}

// В заказе нет товаров.
// products: Этот список не может быть пустым.
{"products": [], "firstname": "Иван", "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

// Ключи есть, но все со значением null.
// firstname, lastname, phonenumber, address: Это поле не может быть пустым.
{"products": [{"product": 1, "quantity": 1}], "firstname": null, "lastname": null, "phonenumber": null, "address": null}

// Не указан номер телефона.
// phonenumber: Это поле не может быть пустым.
{"products": [{"product": 1, "quantity": 1}], "firstname": "Тимур", "lastname": "Иванов", "phonenumber": "", "address": "Москва, Новый Арбат 10"}

// Несуществующий номер телефона.
// phonenumber': Введен некорректный номер телефона.
{"products": [{"product": 1, "quantity": 1}], "firstname": "Тимур", "lastname": "Иванов", "phonenumber": "+70000000000", "address": "Москва, Новый Арбат 10"}

// Заказ с неуществующим id продукта.
// products: Недопустимый первичный ключ "9999"
{"products": [{"product": 9999, "quantity": 1}], "firstname": "Иван", "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

// В поле firstname положили список.
// firstname: Not a valid string.
{"products": [{"product": 1, "quantity": 1}], "firstname": [], "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

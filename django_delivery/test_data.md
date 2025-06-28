// Продукты — это не список, а строка.
// products: Ожидался list со значениями, но был получен "str".
{"products": "HelloWorld", "firstname": "Иван", "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

// Продукты — это null.
// products: Это поле не может быть пустым.
{"products": null, "firstname": "Иван", "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

// Продукты — пустой список.
// products: Этот список не может быть пустым.
{"products": [], "firstname": "Иван", "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

// Продуктов нет.
// products: Обязательное поле.
{"firstname": "Иван", "lastname": "Петров", "phonenumber": "+79291000000", "address": "Москва"}

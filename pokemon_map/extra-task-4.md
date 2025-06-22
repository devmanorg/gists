# Добавьте против чего сильны стихии

Будет удобно, если преимущества стихий будут отображаться прямо на страничке покемона. Сразу станет ясно, нужен этот покемон клану Кирилла или нет.

## Цель

У покемона появятся записи против кого он силён:

![](https://dvmn.org/filer/canonical/1563883999/183/)

## Что понадобится

- [Типы стихий на Вики](https://pokemon.fandom.com/ru/wiki/%D0%A1%D1%82%D0%B8%D1%85%D0%B8%D0%B9%D0%BD%D1%8B%D0%B5_%D1%82%D0%B8%D0%BF%D1%8B)
- `ManyToManyField`
    - [M2M на самого себя](https://stackoverflow.com/questions/15285626/django-self-referential-foreign-key), по аналогии с `ForeignKey`
    - [symmetrical=False](https://docs.djangoproject.com/en/5.2/ref/models/fields/#django.db.models.ManyToManyField.symmetrical)
- Миграции
- Передать эти данные в `show_pokemon`
    - ключ `strong_against`
    - Как значение по ключу нужен список строк с названиями стихий
- Добавить связи между стихиями через админку или `shell`

## Советы

`symmetrical` нужен для того, чтобы если стихия **Травяной** кладёт в ManyToMany стихию **Ядовитый** — у стихии **Ядвитый** в этом поле не повлялся **Травяной**.

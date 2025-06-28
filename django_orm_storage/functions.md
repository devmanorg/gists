## Функция `get_duration`

Функция `get_duration` рассчитывает длительность визита. Она возвращает количество секунд или объект [datetime.timedelta](https://docs.python.org/3.7/library/datetime.html#timedelta-objects) — выберите и реализуйте тот вариант, что считаете лучшим.

```python3
def get_duration(visit):
    # TODO пишите код здесь
    return 0
```

Скопируйте этот фрагмент кода к себе в проект и допишите его.

Эта функция будет использоваться на разных страницах сайта, поэтому лучше её поместить в файл models.py — оттуда её будет проще доставать и эта функция плотно завязана на модель данных. А если вы уже умеете работать с классами в Python, то можете сразу сделать её методом `Visit.get_duration`.

## Функция `format_duration`

Превращает длительность визита в строку, готовит к выводу на страницу.

```python3
def format_duration(duration):
    # TODO пишите код здесь
    return '23ч 59мин'
```

Скопируйте этот фрагмент кода к себе в проект и допишите его. Решите как на странице сайта будет выглядеть продолжительность визита, строка `'23ч 59мин'` в коде выше указана только для примера.

Для работы с объектом `timedelta` вам пригодится эта [статья с примерами](https://python-scripts.com/datetime-time-python).

Будьте осторожны! Атрибут `timedelta.seconds` хранит секунды только за последние сутки и обнуляется после 24 часов. Что с этим делать подробно обсуждается на [StackOverflow](https://stackoverflow.com/questions/51652952/python-timedelta-seconds-vs-total-seconds).

## Пример использования

```python3
from .models import Visit

visit = Visit.objects.all()[0]
duration = get_duration(visit)

print(format_duration(duration))
```

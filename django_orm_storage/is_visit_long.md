Функция `is_visit_long` определяет, подозрителен визит или нет. Возвращает `True` или `False`:

```python3
def is_visit_long(visit, minutes=60):
    # TODO пишите код здесь
    return False
```

Скопируйте этот фрагмент кода к себе в проект и допишите его.

Эта функция будет использоваться на разных страницах сайта, поэтому лучше её поместить в файл models.py — оттуда её будет проще доставать и эта функция плотно завязана на модель данных. А если вы уже умеете работать с классами в Python, то можете сразу сделать её методом `Visit.is_long`.

## Пример использования

```python3
from .models import Visit

visit = Visit.objects.all()[0]
flag = is_visit_long(visit)
```

Можно поменять ограничение и считать визит долгим если тот продлится более 15 минут. Тогда вызов функции будет выглядеть так:

```python3
flag = is_visit_long(visit, minutes=15)
```

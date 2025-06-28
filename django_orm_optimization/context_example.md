# Как сделать кастомный менеджер

Здравствуйте, Юрий. Вы просили рассказать как спрятать фильтрацию постов внутрь кастомного менеджера. Вот короткий гайд:

**1. Пишем запрос**

Вот как отфильтровать все посты по году написания:

```python
year = 2016
posts_at_year = Post.objects.filter(published_at__year=year).order_by('published_at')
```

Достаём посты из 2016 года, потом сортируем по дате.

**2. Прячем в функцию**

Что, если вы захотите использовать этот код в нескольких местах? Нужна функция:

```python
def filter_posts_by_year(posts_query, year):
    posts_at_year = posts_query.filter(published_at__year=year).order_by('published_at')
    return posts_at_year
```

Обратите внимание, что функция принимает на вход `posts_query`. Она принимает на вход **запрос** и возвращает **запрос**. Это даёт супер-гибкость: метод `filter_posts_by_year` начинает работать как обычный `filter`, его можно поместить в любую часть запроса.

Можно отфильтровать все посты:
```python
posts = filter_posts_by_year(Post.objects.all(), 2016)
```
Можно отфильтровать только посты с картинками:
```python
posts_with_imgs = Post.objects.exclude(image__exact='')  # Убрали посты без картинок
posts = filter_posts_by_year(posts_with_imgs, 2016)
```
Также, заметьте, что функция возвращает **запрос**, т.е. его можно уточнять далее:
```python
posts = filter_posts_by_year(Post.objects.all(), 2016)
posts_with_imgs = posts.exclude(image__exact='')
```

Этот запрос будет идентичен предыдущему, где мы фильтровали посты без картинок. Для SQL нет разницы между этими двумя запросами:

- сначала убрать все посты без картинок, потом отфильтровать по году
- сначала отфильтровать все посты по году, потом убрать посты без картинок

**3. Оформить как кастомный менеджер**

Было бы удобно превратить эту функцию в метод `QuerySet`. Его можно будет использовать наравне с `filter`, `exclude`, `annotate` и прочими методами `QuerySet`. А ещё его можно назвать `year`:
```python
Post.objects.exclude(image__exact='').year(2016).annotate(...)
```

Пишем класс QuerySet в файле `models.py`:
```python
class PostQuerySet(models.QuerySet):

    def year(self, year):
        posts_at_year = self.filter(published_at__year=year).order_by('published_at')
        return posts_at_year
```

> Сравните с кодом функции `filter_posts_by_year`. Они ничем не отличаются, только вместо `posts_query` метод кверисета должен принимать `self`.

И подключаем к модели:
```python
class Post(models.Model):
    ...
    objects = PostQuerySet.as_manager()
```

Да, вы только что подменили тот самый `objects`, который всегда следовал после названия модели в запросах: `Post.objects.all()`.

Теперь вы можете пользоваться кастомным кверисетом:
```python
Post.objects.exclude(image__exact='').year(2016).annotate(...)
```

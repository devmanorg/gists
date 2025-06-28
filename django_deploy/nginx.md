# Настройки Nginx

Этот файл настраивает Nginx на раздачу медиа-файлов из папки, которую вы укажете.

Чтобы подключить этот конфиг, создайте любой файл без расширения (например, `starburder`) в папке `/etc/nginx/sites-enabled/` и скопируйте в него конфиг.

**Не забудьте поменять путь до папки с медиа.**

**Путь должен оканчиваться слэшом!** Путь `/some/path` — невалиден, а `/some/path/` — работает.


```conf
# place this file to /etc/nginx/sites-enabled/ folder

server {
    listen 80;
    location /media/ {
        alias /path/to/media/folder/;  # replace the path with yours one
    }
}
```

# spotify-import

Импорт плейлиста из TXT в Spotify через PKCE авторизацию.

## Файлы

- `index.html` — основной импортер, открывать локально
- `callback.html` — редирект после OAuth для GitHub Pages

## Установка

### 1. GitHub Pages

Репозиторий `ym2spotify`: сайт доступен как `https://devurcc.github.io/ym2spotify/`.

Файл `callback.html` в корне ветки публикации → полный адрес колбэка:

`https://devurcc.github.io/ym2spotify/callback.html`

### 2. Настройки Spotify app

На [developer.spotify.com/dashboard](https://developer.spotify.com/dashboard) в настройках вашего приложения:

- Redirect URI: `https://devurcc.github.io/ym2spotify/callback.html`
- Client ID зашит в `index.html`

### 3. Scopes OAuth

Приложение запрашивает: `playlist-modify-public playlist-modify-private user-read-private`. Последний нужен для поля **`country`** в профиле ([документы Spotify](https://developer.spotify.com/documentation/web-api/reference/get-current-users-profile)): по нему в запрос **`GET /v1/search`** подставляется параметр **`market`** (иначе без market и страны каталог считается недоступным). После смены scope обязательна **повторная авторизация**.

### 4. Ошибка 403

**Плейлист:**

- Переавторизуйтесь, чтобы токен содержал актуальные scopes.
- [Dashboard → User management](https://developer.spotify.com/dashboard): в режиме **Development** добавьте аккаунт, с которым входите в приложение.

**Добавление треков в плейлист (403 на `POST …/tracks` или `…/items`):**

- Используется актуальный эндпоинт **`POST /v1/playlists/{id}/items`** ([документы Spotify](https://developer.spotify.com/documentation/web-api/reference/add-items-to-playlist)); старый путь **`…/tracks`** считается deprecated.
- Для приватного плейлиста нужен **`playlist-modify-private`** и приватный профиль; в логе после входа смотрите строку **«Токен scopes»**.

### 5. Использование

1. Откройте `index.html` в браузере (двойной клик)
2. Нажмите «Войти в Spotify» → появится попап → войдите → попап закроется
3. Перетащите TXT файл (формат: `Исполнитель - Песня`, один трек на строку)
4. Введите название плейлиста → «Запустить импорт»

## Формат TXT

```
RADWIMPS - Goshintai
Тату - Нас не догонят
Radiohead - Creep
```

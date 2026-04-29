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

### 3. Ошибка 403 при создании плейлиста

- Войдите заново («Переавторизоваться»), чтобы токен получил scopes `playlist-modify-*`.
- В [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) откройте приложение → **Settings** → **User management**: в режиме **Development** API для сторонних аккаунтов ограничен — добавьте туда **Spotify-логин**, с которым заходите в приложение.

### 4. Использование

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

# spotify-import

Импорт плейлиста из TXT в Spotify через PKCE авторизацию.

## Файлы

- `index.html` — основной импортер, открывать локально
- `callback.html` — страница для `devurcc.github.io/callback`

## Установка

### 1. callback страница

Скопируйте `callback.html` в репозиторий `devurcc.github.io`:

```
devurcc.github.io/
└── callback/
    └── index.html   ← содержимое callback.html
```

Или просто положите `callback.html` в корень как `callback.html` и проверьте что `https://devurcc.github.io/callback` открывается.

### 2. Настройки Spotify app

На [developer.spotify.com/dashboard](https://developer.spotify.com/dashboard) в настройках вашего приложения:

- Redirect URI: `https://devurcc.github.io/callback`
- Client ID зашит в `index.html`

### 3. Использование

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

# Мой нежный органайзер v1.0

Личный PWA-органайзер: задачи, заметки, дедлайны, локальные напоминания, GitHub Sync и выборочная синхронизация с Google Calendar.

## Главная логика

- Все личные задачи и заметки хранятся локально в браузере.
- GitHub Sync хранит резервную копию в `organizer.json`.
- Google Calendar получает только те задачи, где вручную выбран режим Google Calendar.
- Для приватности можно отправлять событие как `Личное дело`, без настоящего названия и описания задачи.
- События из Google Calendar подтягиваются только как занятость на ближайшие 7 дней и не превращаются автоматически в задачи.

## Файлы

- `index.html` — всё приложение.
- `manifest.json` — установка как PWA.
- `sw.js` — офлайн-кэш.
- `icon.svg` — иконка.

## Как опубликовать на GitHub Pages

1. Создать репозиторий, например `personal-organizer`.
2. Загрузить все файлы из архива в корень репозитория.
3. Включить GitHub Pages: Settings → Pages → Deploy from branch → `main` → `/root`.
4. Открыть ссылку вида:

```text
https://vasiekig-droid.github.io/personal-organizer/?v=1
```

## GitHub Sync

В настройках приложения укажи:

- Owner: `vasiekig-droid`
- Repo: `personal-organizer`
- Branch: `main`
- File: `organizer.json`
- Token: твой GitHub token с правом записи в этот репозиторий

На новом устройстве сначала нажимай **Из облака**. **В облако** нажимай только там, где видишь актуальные данные.

## Google Calendar Sync

Нужен Google OAuth Client ID для веб-приложения.

В Google Cloud Console нужно:

1. Создать проект.
2. Включить Google Calendar API.
3. Создать OAuth Client ID типа Web application.
4. Добавить в Authorized JavaScript origins домен GitHub Pages, например:

```text
https://vasiekig-droid.github.io
```

5. Вставить Client ID в настройки приложения.

## Ограничения уведомлений

Локальные уведомления работают лучше, когда приложение открыто или недавно запускалось. Для важных дел с точным временем надёжнее отправлять событие в Google Calendar и использовать его напоминания.

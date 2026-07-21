# AI-помощник методиста — n8n Curriculum Builder

[![n8n](https://img.shields.io/badge/n8n-2.29.8+-blue)](https://n8n.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![GigaChat](https://img.shields.io/badge/GigaChat-API-orange)](https://developers.sber.ru/portal/products/gigachat)

> Автоматизация создания учебных планов, контроля материалов и еженедельной отчётности для методистов онлайн-школ.

---

## 🎯 О проекте

Проект автоматизирует ключевые задачи методиста в EdTech:

| Workflow | Назначение | Результат |
|----------|------------|-----------|
| **Workflow 1** | Генерация учебного плана | Форма → AI (GigaChat) → JSON → Google Sheets |
| **Workflow 2** | Контроль недостающих материалов | Ежедневная проверка → Telegram методисту |
| **Workflow 3** | Итоговый отчёт руководителю | Еженедельная детализация по модулям → Telegram |

**Ключевые возможности:**
- ✅ Генерация структуры курса с целями уроков и материалами
- ✅ Автоматическая проверка загрузки материалов
- ✅ Детализированные отчёты по модулям
- ✅ Логирование всех действий
- ✅ Обработка ошибок с уведомлениями

---

## 🚀 Быстрый старт

### 1. Предварительные требования

- n8n версии **2.29.8** или выше
- Аккаунт Google (для Google Sheets API)
- Telegram Bot (для уведомлений)
- Доступ к GigaChat API (или другой LLM)

### 2. Установка

```bash
# Клонируйте репозиторий
git clone https://github.com/your-username/n8n-ai-curriculum-builder.git
cd n8n-ai-curriculum-builder
```
---

## 3. Импорт воркфлоу в n8n
Откройте ваш n8n instance

Перейдите в Workflows → Import from File

Выберите файлы из папки workflows/:

workflow-01-generate-plan.json

workflow-02-check-materials.json

workflow-03-weekly-report.json

---

## 4. Настройка подключений
Сервис	Что нужно
Google Sheets	OAuth2 авторизация через n8n
Telegram	Токен бота от @BotFather
GigaChat	API-ключ (или замените на другой LLM)
Подробные инструкции — в docs/setup-guide.md.

---

## 5. Создайте таблицы Google Sheets
Импортируйте шаблоны из папки google-sheets/:

CoursePlan — структура учебных планов

CourseLogs — логирование всех действий

---

## 📊 Как это работает
---

## Workflow 1 — Генерация учебного плана

Форма методиста → Валидация → GigaChat (AI) → Очистка JSON → Запись в CoursePlan → Логирование
Методист заполняет форму:

Название курса

Количество модулей (1–20)

Целевая аудитория

Цель курса

AI генерирует структуру с полями:

name — название урока

goal — цель урока

materials — список материалов

---

## Workflow 2 — Контроль материалов

Ежедневно в 10:00 → Чтение CoursePlan → Фильтр (загружено = false) → Группировка → Telegram
Методист получает структурированное сообщение со списком недостающих материалов.

---

## Workflow 3 — Отчёт руководителю

Еженедельно в 09:00 (понедельник) → Чтение CoursePlan → Подсчёт статистики → Telegram
Руководитель получает детализированный отчёт с готовностью по каждому модулю.

---

## 🛠 Технологический стек

   ## Компонент	                    **Назначение**
## n8n (Self-hosted)	    -     Оркестрация всех воркфлоу
## GigaChat	             -     Генерация учебных планов
## Google Sheets	       -     Хранение планов курсов + логирование
## Telegram Bot	       -     Уведомления методисту и руководителю
## HTML + Markdown	    -     Форматирование сообщений
---

##📁 Структура репозитория

## n8n-ai-curriculum-builder/
├── README.md                    # Этот файл
├── LICENSE                      # Лицензия MIT
├── workflows/                   # Экспортированные воркфлоу (.json)
├── docs/                        # Подробная документация
├── google-sheets/               # Шаблоны таблиц
└── examples/                    # Примеры входных данных
---

##🔧 Настройка окружения

В n8n используйте переменные окружения для чувствительных данных:
env
TELEGRAM_BOT_TOKEN=your_bot_token
TELEGRAM_METHODIST_CHAT_ID=123456789
TELEGRAM_MANAGER_CHAT_ID=987654321
GIGACHAT_API_KEY=your_api_key
GOOGLE_SHEETS_DOCUMENT_ID=your_document_id
---

##🐛 Устранение неполадок
Проблема	Решение
Ошибка парсинга JSON от AI	Проверьте, что AI возвращает валидный JSON без плейсхолдеров
Не приходят уведомления в Telegram	Проверьте токен бота и Chat ID
Ошибка записи в Google Sheets	Проверьте OAuth2 авторизацию и права доступа
Подробнее — в docs/troubleshooting.md.

---

##🤝 Вклад в проект
Contributions are welcome! Следуйте CONTRIBUTING.md.

1. Форкните репозиторий

2. Создайте ветку (git checkout -b feature/amazing-feature)

3. Зафиксируйте изменения (git commit -m 'Add amazing feature')

4. Отправьте в ветку (git push origin feature/amazing-feature)

5. Откройте Pull Request

---

##📄 Лицензия
Распространяется под лицензией MIT. См. LICENSE для подробностей.

---

##📬 Контакты
Автор: [Ваше имя]

Email: [ваш email]

Telegram: [ссылка на канал]

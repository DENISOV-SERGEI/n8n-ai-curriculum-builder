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
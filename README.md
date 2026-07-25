# FinGuard Platform

Платформа интеллектуального мониторинга транзакций, антифрода и персонального AI-ассистента для розничных клиентов банка.

**Цель проекта (портфолио):** продемонстрировать компетенции системного аналитика и Solution Architect в финтех-домене: от проектирования API до расчёта unit‑экономики и деплоя в Kubernetes.

---

## 🔧 Технологический стек

### Backend & API
- **FastAPI** (Python 3.11+, async/await, Pydantic)
- **OpenAPI 3.0** – контрактное проектирование, Swagger UI
- **Kafka** – событийный поток транзакций, DLQ, гарантии exactly-once
- **gRPC** (protobuf) – синхронный вызов фрод-скоринга
- **GraphQL** (Strawberry) – клиентский фасад

### Хранение и аналитика
- **PostgreSQL** – основное хранилище транзакций
- **TimescaleDB** – временные ряды и метрики
- **Redis** – кэш идемпотентности
- **Qdrant** – векторная БД для RAG

### AI / ML
- **scikit-learn** – обучение модели антифрода (RandomForest)
- **Qwen2.5** – генерация ответов AI-ассистента
- **sentence-transformers** – эмбеддинги документов

### DevOps & Инфраструктура
- **Docker**, **docker-compose**
- **Kubernetes** (k3d), **Helm**, **Terraform** (базово)
- **GitHub Actions** – CI/CD (lint → test → build → deploy)
- **OpenSearch + Fluent Bit** – централизованное логирование
- **Prometheus + Grafana** – дашборды, алерты
- **k6** – нагрузочное тестирование

### Безопасность
- **JWT/OAuth2**
- **OWASP Top 10** для API
- **HashiCorp Vault** (ознакомительно)

---

## 📐 Архитектура (C4)
_Будет добавлена в процессе – уровни System Context, Containers, Components._

### Ключевые микросервисы
- `transaction-ingest` – приём транзакций, идемпотентность, валидация
- `transaction-simulator` – генератор синтетического потока
- `fraud-detector` – gRPC-сервис фрод-скоринга (ML)
- `rag-assistant` – AI-консультант по тратам
- `graphql-gateway` – единый клиентский API

### Архитектурные паттерны
- DDD (ограниченные контексты, агрегаты)
- CQRS, Event Sourcing (элементы)
- Saga (хореография) для сценариев блокировки
- Idempotency-Key для платёжных операций
- DLQ и retry для устойчивости очередей

---

## 📊 Продуктовые и экономические метрики
- Unit‑экономика: CAC, LTV, ARPU
- TCO (CAPEX + OPEX) и ROI платформы
- Приоритизация фич: WSJF, RICE
- FinOps – расчёт стоимости облачной инфраструктуры

---

## 📝 Архитектурные решения (ADR)
Все ключевые технологические выборы документированы в папке `docs/adr/`:
- [ADR-001](docs/adr/001-fastapi.md) – Выбор веб-фреймворка (FastAPI vs Flask vs DRF)
- _ADR-002 – ADR-015 будут добавляться по мере прохождения модулей_

---

## 📅 Roadmap (модули обучения)

1. **Python и API‑First** – OpenAPI-спецификации, идемпотентность
2. **Контейнеризация** – Docker, k8s, деплой в k3d
3. **CI/CD** – GitHub Actions, Helm, стратегии деплоя
4. **Асинхронные коммуникации** – Kafka, gRPC, GraphQL
5. **Базы данных** – PostgreSQL, TimescaleDB, SQL-аналитика
6. **Архитектура** – DDD, CQRS, Saga, C4, SLO/SLI
7. **ML-интеграции** – обучение и деплой модели фрода
8. **AI‑интеграции** – RAG-пайплайн, Qdrant, YandexGPT
9. **Наблюдаемость и безопасность** – мониторинг, алерты, JWT
10. **Продуктовая аналитика** – unit‑экономика, TCO, ROI
11. **Финал** – портфолио, Architecture Decision Forum

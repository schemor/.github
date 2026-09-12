<p align="center">
  <img src="./assets/schemor-banner.svg" alt="Schemor — бэкенд начинается со схемы данных" width="100%" />
</p>

<p align="center">
  <a href="https://schemor.ru"><img src="https://img.shields.io/badge/schemor.ru-открыть-EF4444?style=for-the-badge" alt="schemor.ru" /></a>
  <a href="https://github.com/schemor/schemor"><img src="https://img.shields.io/badge/основной_проект-GitHub-18181B?style=for-the-badge&logo=github" alt="Основной проект" /></a>
  <a href="https://github.com/schemor/website"><img src="https://img.shields.io/badge/сайт-GitHub-18181B?style=for-the-badge&logo=github" alt="Сайт" /></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/статус-в%20разработке-EF4444?style=flat-square" alt="Статус: в разработке" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white" alt="NestJS" />
  <img src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" alt="React" />
  <img src="https://img.shields.io/badge/MUI-007FFF?style=flat-square&logo=mui&logoColor=white" alt="MUI" />
</p>

---

## Что такое Schemor

**Schemor** — CMS и бэкенд-платформа, в которой схема данных становится основой всей системы.

Вместо того чтобы отдельно собирать модели, CRUD, API, формы, таблицы, валидацию, права доступа и служебную инфраструктуру, разработчик описывает структуру данных, а Schemor использует её как единый источник метаданных.

> **Одна схема → единая модель системы → связанные возможности бэкенда.**

Проект находится в активной разработке. Мы стараемся показывать направление развития открыто и не выдавать запланированные возможности за уже готовые.

<p align="center">
  <img src="./assets/schema-to-backend.svg" alt="Схема данных преобразуется Schemor в API, Admin UI, валидацию, права доступа, поиск и автоматизацию" width="100%" />
</p>

---

## Основная идея

```mermaid
flowchart LR
    A["Схема данных"] --> B["Метаданные Schemor"]

    B --> C["REST API"]
    B --> D["Admin UI"]
    B --> E["Валидация"]
    B --> F["RBAC"]
    B --> G["Поиск"]
    B --> H["Автоматизация"]

    classDef source fill:#16161a,stroke:#ef4444,color:#ffffff,stroke-width:2px;
    classDef core fill:#2a1114,stroke:#ef4444,color:#ffffff,stroke-width:2px;
    classDef output fill:#111114,stroke:#3f3f46,color:#e4e4e7;

    class A source;
    class B core;
    class C,D,E,F,G,H output;
```

Схема данных в Schemor — не просто описание таблиц. Она должна определять поведение связанных частей платформы и уменьшать расхождение между моделью данных, API и административным интерфейсом.

---

## Что мы строим

Schemor развивается вокруг нескольких ключевых направлений:

| Направление | Идея |
|---|---|
| **Динамические сущности** | Создание типов данных, полей и связей без повторения типового CRUD-кода |
| **Динамическая админ-панель** | Интерфейс управления формируется из метаданных сущностей |
| **REST API** | Предсказуемая работа с данными без ручной реализации типовых endpoint'ов |
| **RBAC** | Роли, несколько ролей у пользователя и управляемые разрешения |
| **Поиск** | Поиск по сущностям и справочным данным |
| **Публикация и аудит** | Жизненный цикл контента и история изменений |
| **Автоматизация** | Реакция системы на события через настраиваемые процессы |
| **Расширения** | Плагины, собственные поля, действия, адаптеры и интеграции |

> Некоторые из этих возможностей находятся в разработке, другие запланированы. Актуальные статусы публикуются на [schemor.ru](https://schemor.ru).

---

## Автоматизация процессов

Одна из важных идей Schemor — возможность собирать типовые реакции системы без написания отдельного сервиса для каждого простого сценария.

```mermaid
flowchart LR
    E1["Создан товар"] --> A1["Отправить уведомление"]
    A1 --> A2["Создать запись аудита"]

    E2["Зарегистрирован пользователь"] --> B1["Отправить письмо администратору"]
    B1 --> B2["Создать задачу онбординга"]

    classDef event fill:#2a1114,stroke:#ef4444,color:#fff,stroke-width:2px;
    classDef action fill:#111114,stroke:#52525b,color:#e4e4e7;

    class E1,E2 event;
    class A1,A2,B1,B2 action;
```

В будущем визуальный конструктор процессов должен объединять:

- события;
- условия;
- действия;
- внешние интеграции;
- действия плагинов;
- собственную бизнес-логику.

---

## Архитектурный принцип

```mermaid
flowchart TB
    S["Схема"] --> M["Метаданные"]

    M --> API["API"]
    M --> ADMIN["Admin UI"]
    M --> VALIDATION["Валидация"]
    M --> PERMISSIONS["Права доступа"]
    M --> SEARCH["Поиск"]
    M --> AUTOMATION["Автоматизация"]

    API --> APP1["Web-приложения"]
    API --> APP2["Мобильные приложения"]
    API --> APP3["Внешние сервисы"]

    AUTOMATION --> INT["Интеграции и плагины"]
```

Мы стремимся к тому, чтобы **метаданные были центром системы**, а не побочным описанием уже написанного кода.

---

## Технологии

### Основной продукт

```text
Backend
├── Node.js
├── NestJS
└── TypeScript

Admin UI
├── React
├── react-admin
└── MUI
```

### Публичный сайт

```text
schemor.ru
├── Next.js
├── React
├── TypeScript
└── MUI
```

Архитектура продукта и сайта развивается независимо: публичный сайт не должен зависеть от готовности runtime основной CMS.

---

## Репозитории

<table>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/schemor/schemor">schemor/schemor</a></h3>
      <p><strong>Основной продукт.</strong></p>
      <p>
        Ядро Schemor, бэкенд, Admin UI, метаданные, динамические сущности,
        права доступа, автоматизация и другие возможности платформы.
      </p>
      <p>
        <a href="https://github.com/schemor/schemor">
          <img src="https://img.shields.io/badge/открыть_репозиторий-18181B?style=flat-square&logo=github" alt="Открыть schemor/schemor" />
        </a>
      </p>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/schemor/website">schemor/website</a></h3>
      <p><strong>Публичный сайт проекта.</strong></p>
      <p>
        Лендинг, ранний доступ, публичная дорожная карта, сообщество,
        документация продукта и будущая публичная экосистема Schemor.
      </p>
      <p>
        <a href="https://github.com/schemor/website">
          <img src="https://img.shields.io/badge/открыть_репозиторий-18181B?style=flat-square&logo=github" alt="Открыть schemor/website" />
        </a>
      </p>
    </td>
  </tr>
</table>

---

## Как связаны репозитории

Статусы публичных возможностей не должны обновляться вручную.

```mermaid
flowchart LR
    PLAN["План разработки<br/>schemor/schemor"] --> GEN["Генератор статусов"]
    GEN --> JSON["product-status.json"]
    JSON --> CI["GitHub Actions"]
    CI --> WEB["schemor/website"]
    WEB --> SITE["schemor.ru"]
```

Основной проект остаётся источником фактического состояния разработки, а сайт отвечает за пользовательские тексты и представление этих статусов.

---

## Направления развития

```mermaid
flowchart LR
    F["Основа"] --> A["Admin UI"]
    A --> P["Платформа"]
    P --> AU["Автоматизация"]
    AU --> E["Экосистема расширений"]
    E --> R["Публичный релиз"]
```

Крупные направления:

1. **Основа** — архитектура, метаданные, динамические сущности, аутентификация.
2. **Admin UI** — динамический интерфейс, конструктор типов данных, RBAC, медиа.
3. **Платформа** — локализация, поиск, публикация, аудит.
4. **Автоматизация** — события, условия, действия и визуальный конструктор процессов.
5. **Экосистема** — Plugin SDK, расширения, интеграции и плагины сообщества.
6. **Публичный релиз** — документация, стартовые проекты и доступ для пользователей.

---

## Принципы проекта

- **Схема данных — источник правды.**
- **Метаданные должны приносить практическую пользу, а не существовать ради метаданных.**
- **Типовую инфраструктуру лучше генерировать, чем переписывать в каждом проекте.**
- **Admin UI и API должны следовать одной модели данных.**
- **Простые процессы должны настраиваться декларативно.**
- **Сложные сценарии должны оставаться расширяемыми кодом.**
- **Запланированная возможность всегда должна быть явно отделена от уже готовой.**
- **Архитектура важнее маркетинговых обещаний.**

---

## Для кого Schemor

Schemor создаётся прежде всего для:

- backend-разработчиков;
- frontend-разработчиков, которым нужен headless backend;
- fullstack-разработчиков;
- небольших продуктовых команд;
- разработчиков внутренних систем;
- будущих авторов плагинов и интеграций.

Если вам приходилось снова писать одно и то же вокруг моделей данных, CRUD, прав доступа, форм и административных интерфейсов — мы строим Schemor именно вокруг этой проблемы.

---

## Следить за проектом

<p align="center">
  <a href="https://schemor.ru">
    <img src="https://img.shields.io/badge/Открыть_schemor.ru-EF4444?style=for-the-badge" alt="Открыть schemor.ru" />
  </a>
  &nbsp;
  <a href="https://github.com/schemor/schemor">
    <img src="https://img.shields.io/badge/Следить_за_разработкой-GitHub-18181B?style=for-the-badge&logo=github" alt="Следить за разработкой" />
  </a>
</p>

<p align="center">
  <strong>Бэкенд начинается со схемы данных.</strong>
</p>

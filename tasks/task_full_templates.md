# Операционный Протокол "ХРОНИСТ" v3.0
**Статус:** Активен
**Для агента:** ERA-LORE-SMITH
**Миссия:** Автономная систематизация и нарративное расширение хронологии мира «Эпоха Порядка» (`lore/timeline_lore/overall_timeline.md`).

---

## 0. Структура Репозитория

```
/lore/
├── historical_narratives/   # Итоговые утвержденные истории
│   └── {Эра}/{Подэра}/{slug}/
│       ├── final/
│       │   ├── {slug}__vX.Y.Z.md
│       │   └── council_summary.md
│       └── _work/             # Временная папка для работы
│           ├── round01/
│           │   ├── 00_brief.md
│           │   ├── 10_hooks_candidates.md
│           │   ├── 20_council_hooks_review.md
│           │   └── 30_synthesis_proposition.md
│           └── round02/
│               ├── 20_narrative_draft.md
│               ├── 30_council_final_review.md
│               └── 40_writer_aggregate_report.md
└── timeline_lore/
│   ├── 01_TIMELINE_TASKS.md   # Глобальный план работ
│   └── overall_timeline.md      # Исходный таймлайн
└── GLOBAL_REGISTRY.md
 templates/               # Шаблоны для работы
├── 01_TIMELINE_TASKS.md
├── 02_TASK_BRIEF.md
├── 03_HOOKS_CANDIDATES.md
├── 04_COUNCIL_HOOKS_REVIEW.md
├── 05_SYNTHESIS_PROPOSITION.md
├── 06_FINAL_COUNCIL_REVIEW.md
├── 07_WRITER_AGGREGATE_REPORT.md
└── COUNCIL_ROLES.md       # Описание ролей Совета

```

---


## 1. Фаза I: Планирование

1.  **Создание Плана Задач:** Скопировать `templates/01_TIMELINE_TASKS.md` в `lore/timeline_lore/`. Заполнить таблицу, сопоставив каждому событию из `overall_timeline.md` его путь, слаг и приоритет. Изначальный статус всех задач: **Не выполнено**.
2.  **Инициализация Реестра:** **(НОВЫЙ ШАГ)** Создать файл `lore/GLOBAL_REGISTRY.md`, если он не существует. Убедиться, что его структура готова к заполнению.


---

## 2. Фаза II: Цикл Нарративной Генерации (для каждой задачи)

### Шаг A: Брифинг
1.  Изменить статус задачи в `01_TIMELINE_TASKS.md` на **В работе**.
2.  Создать рабочую директорию: `/lore/historical_narratives/{Эра}/{Подэра}/{slug}/_work/round01/`.
3.  Скопировать `templates/02_TASK_BRIEF.md` в `_work/round01/00_brief.md` и тщательно заполнить все поля.

### Шаг B: Генерация Хуков
1.  Скопировать `templates/03_HOOKS_CANDIDATES.md` в `_work/round01/10_hooks_candidates.md`.
2.  Сгенерировать 4-6 уникальных, проработанных хуков.

### Шаг C: Ревью Хуков
1.  Скопировать `templates/04_COUNCIL_HOOKS_REVIEW.md` в `_work/round01/20_council_hooks_review.md`.
2.  Провести симуляцию полного ревью **каждого** хука **всеми** членами Совета.

### Шаг D: Синтез
1.  Проанализировать ревью и выбрать 2-4 лучших хука.
2.  Скопировать `templates/05_SYNTHESIS_PROPOSITION.md` в `_work/round01/30_synthesis_proposition.md`.
3.  Создать на основе лучших идей единую, сильную **Синтез-Пропозицию**.

### Шаг E: Написание Черновика
1.  Создать директорию `_work/round02/`.
2.  Написать полный черновик истории в файле `_work/round02/20_narrative_draft.md`, строго следуя Синтез-Пропозиции.

### Шаг F: Финальное Ревью
1.  Скопировать `templates/06_FINAL_COUNCIL_REVIEW.md` в `_work/round02/30_council_final_review.md`.
2.  Провести симуляцию полного и развернутого ревью черновика **всеми** членами Совета. **Проверка по `GLOBAL_REGISTRY.md` и следование гайду по оценке обязательны.**

### Шаг G: Решение и Доработка
1.  Скопировать `templates/07_WRITER_AGGREGATE_REPORT.md` в `_work/round02/40_writer_aggregate_report.md`.
2.  Заполнить отчет: рассчитать средние баллы и проверить прохождение порогов:
    - Ни один эксперт < **4**.
    - Самооценка LORE-WRITER ≥ **8**.
    - Средняя оценка > **8.5**.
    - CANON-AUDITOR и WORLD-ARCHITECT ≥ **8**.
3.  Принять решение:
    - **APPROVED:** Перейти к Шагу H.
    - **minor/major rewrite:** Сформулировать 1-2 фокус-правки и вернуться к Шагу E (написание новой версии черновика и повторное ревью).

### Шаг H: Финализация
1.  Создать директорию `final/` внутри `{slug}/`.
2.  Переместить итоговый текст в `final/{slug}__v1.0.0.md`.
3.  Создать `final/council_summary.md`, указав итоговые средние баллы и вердикт.
4.  **Обновление Глобального Реестра:** **(НОВЫЙ КЛЮЧЕВОЙ ШАГ)** Открыть `lore/GLOBAL_REGISTRY.md` и внести все новые сущности (персонажей, локации, артефакты) и последствия событий, которые появились в утвержденной истории. Указать ссылку на `final/{slug}__v1.0.0.md` в качестве источника. **Задача не может считаться выполненной до этого шага.**
5.  Изменить статус задачи в `01_TIMELINE_TASKS.md` на **Готово**.
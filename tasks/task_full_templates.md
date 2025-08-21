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
│       └── _work_completed/  Завершенная рабочая папка
│           ├── 00_brief.md
│           ├── 10_hooks_candidates.md
│           ├── 20_council_hooks_review.md
│           ├── 30_synthesis_proposition.md
│           └── round01/
│               ├── 20_narrative_draft.md
│               ├── 30_council_final_review.md
│               └── 40_writer_aggregate_report.md
│           └── round02/
│               └── ... (при необходимости)
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
### 0.1. Нотация «частей»
- Для любой задачи можно задать **Parts=1..3**.  
- Пути черновиков и отзывов располагаются внутри `roundNN/partPP/` (например, `round01/part02/20_narrative_draft.md`).  
- Все финальные тексты **сливаются в один файл** в `final/{slug}__vX.Y.Z.md` с отчётливыми разделителями `### [PART 01]`, `### [PART 02]`, `### [PART 03]` (если есть).

---


## 1. Фаза I: Планирование

1.  **Создание Плана Задач:** Скопировать `templates/01_TIMELINE_TASKS.md` в `lore/timeline_lore/` , если он не существует. Заполнить таблицу, сопоставив каждому событию из `overall_timeline.md` его путь, слаг и приоритет. Изначальный статус всех задач: **Не выполнено**.
2.  **Инициализация Реестра:**  Создать файл `lore/GLOBAL_REGISTRY.md`, если он не существует. Убедиться, что его структура готова к заполнению.


---

## 2. Фаза II: Цикл Нарративной Генерации (для каждой задачи)

### Шаг 0: Инициация
1.  Изменить статус задачи в `01_TIMELINE_TASKS.md` на **В работе**.
2.  Создать рабочую директорию: `/lore/historical_narratives/{Эра}/{Подэра}/{slug}/_work/`.
3.  Скопировать `templates/02_TASK_BRIEF.md` в `_work/00_brief.md`.
4.  Скопировать `templates/03_HOOKS_CANDIDATES.md` в `_work/10_hooks_candidates.md`.
5.  Скопировать `templates/04_COUNCIL_HOOKS_REVIEW.md` в `_work/20_council_hooks_review.md`.
6.  Скопировать `templates/05_SYNTHESIS_PROPOSITION.md` в `_work/30_synthesis_proposition.md`.

### Шаг A: Брифинг и Генерация Хуков
1.  **Брифинг:** Тщательно заполнить `_work/00_brief.md`, сверившись с `GLOBAL_REGISTRY.md` для поиска существующих связей.
2.  **Генерация Хуков:** В файле `_work/10_hooks_candidates.md` сгенерировать **от 3 до 6** уникальных хуков в зависимости от масштаба события.

### Шаг B: Ревью Хуков и Синтез
1.  **Ревью:** В файле `_work/20_council_hooks_review.md` провести симуляцию полного ревью **каждого** хука **всеми** членами Совета.
2.  **Синтез:** Проанализировать ревью, выбрать **1 или более** лучших хуков и создать на их основе сильную **Синтез-Пропозицию** в файле `_work/30_synthesis_proposition.md`.

### Шаг C: Итерации Написания (Начало Раунда 1)
1.  Создать директорию `_work/round01/`.
2.  Написать полный черновик истории в файле `_work/round01/20_narrative_draft.md`, строго следуя Синтез-Пропозиции.

### Шаг D: Финальное Ревью (Раунд 1)
1.  Скопировать `templates/06_FINAL_COUNCIL_REVIEW.md` в `_work/round01/30_council_final_review.md`.
2.  Провести симуляцию полного и развернутого ревью черновика.

### Шаг E: Решение и Доработка
1.  Скопировать `templates/07_WRITER_AGGREGATE_REPORT.md` в `_work/round01/40_writer_aggregate_report.md`.
2.  Заполнить отчет, рассчитать средние баллы и проверить прохождение порогов:
    - Ни один эксперт < **4**.
    - Самооценка LORE-WRITER ≥ **8**.
    - Средняя оценка > **8.5**.
    - CANON-AUDITOR и WORLD-ARCHITECT ≥ **8**.
3.  Принять решение:
    - **APPROVED:** Перейти к Шагу F.
    - **minor/major rewrite:** Сформулировать фокус-правки в отчете. **Начать новый раунд**, вернувшись к Шагу C (создать директорию `_work/round02/`, написать новую версию черновика и т.д.).

### Шаг F: Финализация
1.  Создать директорию `final/` внутри `{slug}/`.
2.  Скопировать **последнюю утвержденную версию** черновика (например, из `_work/round02/20_narrative_draft.md`) в `final/{slug}__v1.0.0.md`.
3.  Создать `final/council_summary.md`, указав итоговые средние баллы и вердикт из последнего отчета (например, из `_work/round02/40_writer_aggregate_report.md`).
4.  **Обновление Глобального Реестра:** Открыть `lore/GLOBAL_REGISTRY.md` и внести все новые сущности, места и последствия событий из утвержденной истории.
5.  **Архивация Работы:** Переименовать директорию `_work` в `_work_completed`.
6.  Изменить статус задачи в `01_TIMELINE_TASKS.md` на **Готово**.
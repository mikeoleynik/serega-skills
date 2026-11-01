# serega-skills

Скиллы [AskSerega](https://askserega.ru): по одному фреймворку на слэш-команду. Скилл пишет артефакт в `.theory/` того репозитория, где его вызвали.

Плагин обновляется сам. [skills.sh](https://skills.sh) копирует файлы в проект, и их обновляют вручную. На одного агента выбирай один способ: оба сразу поставят каждый скилл дважды.

## Установка

Репозиторий ещё не опубликован. Пока ставится с локального пути:

```bash
npx skills@latest add /абсолютный/путь/к/serega-skills
```

После публикации на GitHub адрес в командах ниже — `<owner>/serega-skills`.

### Cursor и любой агент из skills.sh

```bash
npx skills@latest add <owner>/serega-skills -a cursor
```

Без `-a` установщик спросит, в какие агенты ставить. Чтобы взять один скилл:

```bash
npx skills@latest add <owner>/serega-skills --skill data-flow-mapping
```

Обновление: `npx skills@latest update`. Новый скилл подхватывается повторным `add`.

### Codex

```bash
codex plugin marketplace add <owner>/serega-skills
codex plugin add serega-skills@serega-skills
```

Обновляется при запуске.

### GitHub Copilot (CLI и VS Code)

```bash
copilot plugin marketplace add <owner>/serega-skills
copilot plugin install serega-skills@serega-skills
```

Один раз добавь в `~/.copilot/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "serega-skills": {
      "source": { "source": "github", "repo": "<owner>/serega-skills" },
      "autoUpdate": true
    }
  }
}
```

В VS Code: **Chat: Install Plugin From Source** и URL репозитория.

### Claude Code

```bash
claude plugin marketplace add <owner>/serega-skills
claude plugin install serega-skills@serega-skills
```

Либо тот же `npx skills add`, если нужен редактируемый файл, а не подписка на плагин.

### Gemini CLI

```bash
gemini skills install https://github.com/<owner>/serega-skills.git --path skills
```

Повтор команды обновляет файлы.

## Скиллы

| Команда | Что пишет |
| --- | --- |
| `/data-flow-mapping` | `.theory/data-flow-mapping/<сущность>.md` — маршрут одной сущности: первоисточник, копии, события, побочные эффекты |
| `/adr` | `.theory/adr/<решение>.md` — одно принятое решение: контекст, варианты, выбор и последствия |
| `/anti-corruption-layer` | `.theory/anti-corruption-layer/<сервис>-<внешняя-система>.md` — перевод между своим сервисом и внешней системой: модели, маппинг, порты |
| `/architecture-decision-mapping` | `.theory/architecture-decision-mapping/index.md` — хронология решений системы: триггеры, замены, фитнес-функции, слепые зоны |
| `/bounded-context-mapping` | `.theory/bounded-context-mapping/index.md` — карта ограниченных контекстов системы или домена: зоны смысла, связи, конфликты терминов |
| `/c4-model` | `.theory/c4-model/index.md` — модель C4 системы: контекст, контейнеры, компоненты одного контейнера, код критического места |
| `/characterization-testing` | `.theory/characterization-testing/<модуль>.md` — текущее поведение модуля или endpoint и код характеризационных тестов |
| `/context-mapping` | `.theory/context-mapping/index.md` — связи ограниченных контекстов системы: направление, паттерн, ACL и протекание модели |
| `/contract-testing` | `.theory/contract-testing/<consumer>-<provider>.md` — контракт пары сервисов: схема, примеры payload и шаблоны тестов |
| `/conway-mapping` | `.theory/conway-mapping/index.md` — команды, контексты и сервисы системы и шаги выравнивания границ |
| `/ddd-bounded-contexts` | `.theory/ddd-bounded-contexts/<сервис>.md` — ограниченные контексты сервиса: субдомен, агрегаты, границы и серые зоны; для системы целиком — `index.md` |
| `/dependency-mapping` | `.theory/dependency-mapping/<сервис-или-модуль>.md` — зависимости одного сервиса или модуля: направление связей и критические узлы |
| `/event-driven-architecture` | `.theory/event-driven-architecture/<сценарий>.md` — событийная интеграция сценария или ограниченного контекста: события, схемы, гарантии и пилот |
| `/event-storming` | `.theory/event-storming/<процесс>.md` — события, команды, агрегаты и узкие места одного процесса |
| `/evolutionary-architecture` | `.theory/evolutionary-architecture/index.md` — характеристики системы, фитнес-функции, нарушения и первая проверка в CI |
| `/hexagonal-architecture` | `.theory/hexagonal-architecture/<сервис-или-модуль>.md` — ядро, порты, адаптеры и нарушения границ одного сервиса или модуля |
| `/modular-monolith` | `.theory/modular-monolith/index.md` — модули одной системы: фасады, запрет сквозных импортов и проверка границ |
| `/refactoring-patterns` | `.theory/refactoring-patterns/<модуль-или-класс>.md` — план рефакторинга одного модуля или класса: запах, приёмы, метрики и код до и после |
| `/reference-architecture` | `.theory/reference-architecture/index.md` — эталон одной организации или платформы: слои, соответствие сервиса и проверяемые правила |
| `/responsibility-mapping` | `.theory/responsibility-mapping/index.md` — карта ответственности системы: обязанности, владельцы и сиротские функции; для одного сервиса — `<сервис>.md` |
| `/rfc-process` | `.theory/rfc-process/<кейс>.md` — RFC одного изменения: критерии, жизненный цикл и заполненный документ. PR и исходники не трогает |
| `/runtime-flow-mapping` | `.theory/runtime-flow-mapping/<сценарий>.md` — путь одного сценария: шаги, транспорт, состояние и точки отказа |
| `/sequence-diagrams` | `.theory/sequence-diagrams/<сценарий>.md` — порядок сообщений одного сценария: участники, стрелки и граничные случаи |
| `/stable-dependencies-principle` | `.theory/stable-dependencies-principle/index.md` — нестабильность модулей системы и нарушения SDP; для одного модуля — `<модуль>.md` |
| `/strangler-fig-pattern` | `.theory/strangler-fig-pattern/<домен>.md` — план выделения домена из монолита. Имя монолита в заголовке. Исходники, фасад и PR не трогает |
| `/system-context-mapping` | `.theory/system-context-mapping/<сервис>.md` — сервис как чёрный ящик: акторы, внешние системы и потоки |
| `/system-quality-attributes` | `.theory/system-quality-attributes/index.md` — приоритеты quality attributes системы, конфликтующие пары и анти-цели |
| `/system-theory-anchor` | `.theory/system-theory-anchor/index.md` — аксиомы системы: инвариант, боль и запреты на ревью |
| `/team-topologies` | `.theory/team-topologies/index.md` — типы команд, владение сервисами и режимы взаимодействия организации или платформы |
| `/theory-graph` | `.theory/theory-graph/index.md` — граф документов проекта: связи, слепые зоны и что создать; для одного сервиса — `<сервис>.md` |
| `/ubiquitous-language` | `.theory/ubiquitous-language/<домен-или-сервис>.md` — термины домена, запрещённые синонимы и имена в коде |
| `/uml-basics` | `.theory/uml-basics/<модуль>.md` — классы, последовательность сценария и деятельность процесса одного модуля |
| `/wardley-mapping` | `.theory/wardley-mapping/index.md` — стадии эволюции компонентов системы, зависимости и три шага |
| `/zachman-framework` | `.theory/zachman-framework/index.md` — матрица 6×6 системы: шесть вопросов на шести уровнях |

Каталог `.theory/` появляется при первой записи. Его коммитят вместе с репозиторием.

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

Каталог `.theory/` появляется при первой записи. Его коммитят вместе с репозиторием.

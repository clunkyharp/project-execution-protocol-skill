# project-execution-protocol-skill

Публичный репозиторий со skill `project-execution-protocol` для Codex.
Этот skill нужен для строго организованного выполнения задач в репозитории: чёткие границы scope, минимальные правки, контролируемая проверка и короткие рабочие отчёты.

## Структура репозитория

```text
project-execution-protocol-skill/
├─ README.md
├─ LICENSE.txt
└─ skills/
   └─ project-execution-protocol/
      ├─ SKILL.md
      └─ agents/
         └─ openai.yaml
```

## Установка

Установка по URL папки skill:

```bash
$skill-installer install https://github.com/clunkyharp/project-execution-protocol-skill/tree/main/skills/project-execution-protocol
```

После установки перезапустите Codex.

Альтернативно через `repo/path`:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo clunkyharp/project-execution-protocol-skill \
  --path skills/project-execution-protocol
```

## Содержимое

- `skills/project-execution-protocol/SKILL.md` — правила работы skill: intake, границы scope, порядок выполнения, проверка, формат отчёта.
- `skills/project-execution-protocol/agents/openai.yaml` — отображаемое имя, короткое описание и prompt для интерфейса.

## Лицензия

Репозиторий распространяется по лицензии MIT. См. файл `LICENSE.txt`.

# Wippli Prompts — branch: `prompts`

This branch holds Claude system prompts per client product.
The `main` branch holds WipBoard HTML templates.

## Structure

```
moorestrat/
  └── system-prompt.md      # System prompt for MooreStrat Claude runs
```

## n8n integration

The Moore workflow (`H6Pb0WUyVGcDSDT5`) has a GitHub node that fetches
`moorestrat/system-prompt.md` from this branch at runtime, then feeds
it into the `Prompt Template` Set node via `{{ $json.content }}`.

## Editing

Edit directly on GitHub or via PR. Changes take effect on the next
workflow run — no n8n touch needed.

## Adding a new client

1. Create folder `clientname/`
2. Add `system-prompt.md` inside
3. Duplicate the n8n GitHub fetch node, point it to the new path

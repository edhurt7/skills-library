# Pack Template

Use this template to create a new pack in `packs/`.

## Steps

1. Copy `templates/pack-template/` to `packs/<pack-name>/`.
2. Update `packs/<pack-name>/README.md` with the pack purpose, scope, and usage.
3. Add skill files under `skills/` using the format in `skills/01_skill.md`.
4. Populate `examples/` with minimal, runnable examples.
5. Fill in `benchmark/benchmark_table.md` after running evaluations.
6. Write the tutorial in `tutorial/tutorial_writeup.md`.

## Expectations

- Keep content concise and reproducible.
- Use clear naming and stable paths.
- Avoid large binaries; link to external artifacts if needed.

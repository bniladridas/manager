<p align="center">
  <img src="https://raw.githubusercontent.com/Coccinella-Labs/manager/main/.github/assets/thumbnail.png" alt="manager" width="100%">
</p>

make recipe runner.

Python recipe runner (`manager/` package with `Manager` class and `cli.py`): runs project recipes, sets up git hooks for conventional commits, and renders from `templates/`.

## Run

```bash
make install      # install
make test         # tests
make lint         # lint
make check        # lint + test
```

See `ARCHITECTURE.md` and `MIGRATION.md` for design and migration notes.

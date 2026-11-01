# OpenOptOut Brokers (`openoptout-brokers`)

Official community catalog of data broker opt-out add-ons for [OpenOptOut](https://github.com/rlnunez/OpenOptOut).

Each data broker is defined as a pure declarative plugin in its own folder under `brokers/<id>/`, containing:
- `manifest.json`: Metadata, version, and broker ID.
- `spec.json`: Declarative opt-out steps (`navigate`, `fill`, `click`, `pause_for_human`, `expect_success`).
- `README.md`: Information about the broker and opt-out process.

## Repository Layout
```
├── brokers/              # 80+ vetted broker add-ons
│   ├── spokeo/
│   ├── beenverified/
│   ├── radaris/
│   └── ...
├── _template/            # Starter template for adding a new broker
└── tools/                # Validation and packaging tools
    ├── validate.py       # Syntax, schema, and dry-run validator
    └── package.py        # Generates uploadable zip archives
```

## Adding or Updating a Broker
1. Copy `_template/` to `brokers/<id>/`.
2. Follow the broker specification rules in `tools/validate.py`.
3. Never include SSNs, government IDs, or real personal information.
4. Test your spec:
   ```bash
   python3 tools/validate.py <id>
   ```

## Releases & Versioning
When publishing an update to a broker, use GitHub Releases:
- Monorepo tag format: `{broker_id}-v{version}` (e.g., `spokeo-v1.1.0`).
- Mark test builds as pre-releases so conservative OpenOptOut instances ignore them until ready.

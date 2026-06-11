<!--
 Licensed to the Apache Software Foundation (ASF) under one
 or more contributor license agreements.  See the NOTICE file
 distributed with this work for additional information
 regarding copyright ownership.  The ASF licenses this file
 to you under the Apache License, Version 2.0 (the
 "License"); you may not use this file except in compliance
 with the License.  You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing,
 software distributed under the License is distributed on an
 "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
 KIND, either express or implied.  See the License for the
 specific language governing permissions and limitations
 under the License.
-->
# Contributing to Apache Superset

Contributions are welcome and are greatly appreciated! Every
little bit helps, and credit will always be given.

## Developer Portal

All developer and contribution documentation has moved to the Apache Superset Developer Portal:

**[📚 View the Developer Portal →](https://superset.apache.org/developer_portal/)**

The Developer Portal includes comprehensive guides for:
- [Contributing Overview](https://superset.apache.org/developer_portal/contributing/overview)
- [Development Setup](https://superset.apache.org/developer_portal/contributing/development-setup)
- [Submitting Pull Requests](https://superset.apache.org/developer_portal/contributing/submitting-pr)
- [Contribution Guidelines](https://superset.apache.org/developer_portal/contributing/guidelines)
- [Code Review Process](https://superset.apache.org/developer_portal/contributing/code-review)
- [Development How-tos](https://superset.apache.org/developer_portal/contributing/howtos)

Source for the Developer Portal documentation is [located here](https://github.com/apache/superset/tree/master/docs/developer_portal).

## Quick Lint & Type-Check Reference

Before opening a pull request you can run focused checks against individual
files. This is much faster than a full `pre-commit run --all-files`.

### Python (backend)

```bash
# Lint a single file
ruff check superset/path/to/file.py

# Auto-fix lint issues
ruff check --fix superset/path/to/file.py

# Check formatting
ruff format --check superset/path/to/file.py

# Auto-fix formatting
ruff format superset/path/to/file.py

# Type-check a single file
mypy superset/path/to/file.py

# Or use pre-commit to run any hook on specific files
pre-commit run ruff --files superset/path/to/file.py
pre-commit run mypy --files superset/path/to/file.py
```

### TypeScript / JavaScript (frontend)

```bash
cd superset-frontend

# Lint a single file
npx oxlint --config oxlint.json src/path/to/file.ts

# Auto-fix lint issues
npx oxlint --config oxlint.json --fix src/path/to/file.ts

# Check formatting
npx prettier --check src/path/to/file.ts

# Auto-fix formatting
npx prettier --write src/path/to/file.ts

# Type-check the frontend project (single-file mode is not supported by tsc)
npm run type
```

### Using pre-commit on staged changes

```bash
# Stage your changes, then run all hooks on only those files
git add superset/path/to/file.py
pre-commit run            # runs every hook, but only on staged files

# Or run a single hook
pre-commit run ruff       # Python lint (staged files only)
pre-commit run mypy       # Python type-check (staged files only)
pre-commit run prettier-frontend  # Frontend formatting (staged files only)
pre-commit run oxlint-frontend    # Frontend lint (staged files only)
```

> **Tip:** Install the hooks once with `pre-commit install` so they run
> automatically on every `git commit`.

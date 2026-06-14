# weather-agent

## Dependency rules

**Changing any Mastra dependency version is FORBIDDEN.** Do not bump, upgrade,
downgrade, or re-pin `@mastra/core` away from `1.24.1`, and do not modify the version
of any other `@mastra/*` package or `mastra` in `package.json` or in any lockfile
(`package-lock.json`, `pnpm-lock.yaml`).

### The pinned, working set (do not change)

```
@mastra/core           1.24.1
@mastra/deployer       1.24.0   <- load-bearing
@mastra/server         1.24.0   <- load-bearing
@mastra/evals          1.2.1
@mastra/libsql         1.8.0
@mastra/loggers        1.1.1
@mastra/memory         1.15.0
@mastra/observability  1.8.0
mastra (CLI)           1.4.1
```

`@mastra/deployer` and `@mastra/server` are pinned to `1.24.0` **on purpose** and listed
as direct dependencies. Versions `>= 1.30`-era import `@mastra/core/agent/durable`, which
does not exist in `core@1.24.1` — letting them float to latest crashes the built server
with `ERR_MODULE_NOT_FOUND: @mastra/core/dist/agent/durable/index.js`. Keep them pinned.

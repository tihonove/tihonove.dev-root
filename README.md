# tihonove.dev-root

Страница-визитка на https://tihonove.dev.

- `site/` — статика, отдаётся `nginx-unprivileged` на порту 8080 (`Dockerfile`).
- `deploy/` — kustomize-манифесты; Flux из [tihonove.dev-apps](https://github.com/tihonove/tihonove.dev-apps) (`apps/root.yaml`) следит за `main:./deploy`.
- CI (`.github/workflows/ci.yaml`): на push в `main` собирает образ `ghcr.io/tihonove/tihonove.dev-root:<short-sha>` под amd64+arm64, затем коммитит новый тег в `deploy/kustomization.yaml` — это и есть деплой.

Откат: `git revert` коммита `deploy: <sha>`.

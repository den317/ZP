<!-- DEN317-REPOSITORY-SYNC:START -->
## Repository freshness and cross-computer handoff

These rules cover repository synchronization only; preserve this project's existing domain rules, generated-instruction sources, review gates and publication permissions.

- Before each new task, resumption on another computer, or change of repository/branch, inspect the branch, working tree and in-progress Git operations; fetch current `origin` branches and tags. Resolve the task's intended branch and record its exact commit. Do not repeat this before every individual read/edit.
- On the configured Windows PC, run `C:\projects\.repo-sync\Before-Task.ps1 -Repository <repository-path> -Update` with PowerShell 7 and inspect its JSON/exit code. Without this helper, run the equivalent Git checks. Exit 0 means ready; 2 means local state needs attention; 3 means freshness could not be established. A background hourly fetch does not update working files.
- Integrate upstream automatically only at task startup, in a clean working tree, without an active merge/rebase/cherry-pick/bisect, and only by fast-forward to the inspected upstream commit (`git merge --ff-only <sha>`). Do not switch another task's branch. If dirty, diverged, detached or lacking an upstream, preserve the state and explain the required resolution. A fetch/network failure means freshness is UNKNOWN, not verified; read-only offline work may continue with that limitation stated.
- Prefer a separate task branch (and a separate worktree for simultaneous local writers). Preserve existing repository rules for PRs, direct-main changes, acceptance and commits. Never automatically stash, discard changes, reset hard, force-push, delete refs or publish unrelated work to achieve synchronization. Hourly automation must only fetch and report.
- Web/API agents: read this instruction and task files from one freshly resolved branch commit, rather than from chat memory. Immediately before writing, re-read the target branch head and relevant file/blob SHA; use the connector's conditional-write/expected-SHA mechanism where supported. If the base changed, re-read and recompute the patch; do not overwrite the concurrent change. If a safe conditional update is unavailable, use a new branch/PR and report that limitation.
- Before an authorized push/publication, refresh the remote state and review the exact staged diff. Use an ordinary push; if rejected, fetch and reconcile explicitly. Before moving to another computer, send the authorized commits to GitHub (or clearly report that work remains local). Finish with branch, commit/PR, validation actually run, and any unpublished or conflicting changes. Never claim GitHub is updated from a local-only commit or an unmerged PR.
<!-- DEN317-REPOSITORY-SYNC:END -->

# ZP — Правила для Claude Code

> **Тип:** Base/Принципы | **Source-of-truth:** нулевые принципы + карта иерархии

## Структура

```
ZP/
├── README.md              ← обзор + навигация
├── hierarchy.md           ← карта иерархии 0→1→2→3
├── principles/            ← по файлу на принцип
│   ├── ZP.1-axiomaticity.md
│   ├── ZP.2-structure-and-symmetry.md
│   ├── ZP.3-multiscale.md
│   ├── ZP.4-optimization.md
│   ├── ZP.5-probability-and-information.md
│   └── ZP.6-computational-limits.md
└── CLAUDE.md              ← этот файл
```

## Правила

1. **Список принципов открыт.** Текущие 6 (ZP.1-ZP.6) — ядро, но новые принципы могут быть добавлены при обнаружении транс-дисциплинарных мета-ограничений. Критерий: принцип работает во ВСЕХ доменах (физика, биология, общество, IT, мышление). Кандидаты: метакогниция/рекурсивное самомоделирование, нишевое конструирование, пластичность-стабильность.
2. **Контент растёт внутри файлов.** Добавляй примеры, нарушения, связи — но в существующие файлы принципов.
3. **Шаблон файла принципа:** Определение → Следствие → Примеры применения → Типичные нарушения → Связь с FPF.
4. **hierarchy.md** — единственное место для карты иерархии. Не дублируй в README.
5. **README** — только обзор и навигация. Не дублируй содержание принципов.

# Interpreted-Context-Methdology

ICM is a framework for building structured, multi-stage AI workflows out of markdown files and folder conventions. Each workspace gives AI agents the right context at each stage of a task, and gives humans clear edit surfaces between stages.

## Folder Map

```
model-workspace-protocol/
├── CLAUDE.md                          (you are here)
├── README.md                          (project overview)
├── LICENSE
├── _core/                             (shared conventions and templates)
│   ├── CONVENTIONS.md                 (source of truth for all patterns)
│   ├── placeholder-syntax.md          (how {{VARIABLES}} work)
│   ├── target-repo-detection.md       (identify a target repo from cwd)
│   ├── stack-and-rules-detection.md   (read any repo's stack and project rules)
│   └── templates/                     (blank starting points for new workspaces)
└── workspaces/
    ├── script-to-animation/           (content idea -> animated video)
    ├── course-deck-production/        (unstructured material -> course PowerPoints)
    ├── release-notes/                 (git history -> user-facing changelog)
    ├── tutorials/                     (feature -> blog post and/or video script)
    ├── marketing-video/               (product -> conversion-focused marketing video, Hormozi-based)
    ├── feature-pipeline/              (brief -> design -> implement -> review for any external repo)
    ├── adversarial-audit/             (find broken-assumption bugs in any external repo)
    └── workspace-builder/             (builds new MWP workspaces)
```

## Routing

| You want to... | Go to |
|-----------------|-------|
| Create content with script-to-animation | `workspaces/script-to-animation/CLAUDE.md` |
| Build course slide decks from source material | `workspaces/course-deck-production/CLAUDE.md` |
| Generate release notes from any git repo | `workspaces/release-notes/CLAUDE.md` |
| Write a tutorial about any project feature | `workspaces/tutorials/CLAUDE.md` |
| Build a marketing video for any product (Hormozi method) | `workspaces/marketing-video/CLAUDE.md` |
| Run a feature pipeline (brief -> design -> implement -> review) on any external repo | `workspaces/feature-pipeline/CLAUDE.md` |
| Run an adversarial audit on any external repo | `workspaces/adversarial-audit/CLAUDE.md` |
| Build a new workspace for any domain | `workspaces/workspace-builder/CLAUDE.md` |
| Read the full MWP specification | `_core/CONVENTIONS.md` |
| Understand the placeholder system | `_core/placeholder-syntax.md` |
| Detect the target repo from cwd (cross-repo workspaces) | `_core/target-repo-detection.md` |
| Detect stack and project rules in any repo | `_core/stack-and-rules-detection.md` |
| Use a template for a new workspace | `_core/templates/` |

## Triggers

| Keyword | Action |
|---------|--------|
| `setup` | Run onboarding in whatever workspace you are in |
| `status` | Show pipeline completion for the current workspace |

## How It Works

Each workspace is self-contained with its own CLAUDE.md. Navigate into a workspace folder and that workspace's CLAUDE.md takes over. You do not need to read this root file once you are inside a workspace.

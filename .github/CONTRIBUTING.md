# Contributing to TemanDonor

Thank you for your interest in contributing! 🩸

## Getting Started
1. Fork the repository you want to contribute to
2. Create a new branch from `dev`
3. Make your changes
4. Submit a Pull Request to `dev`

## Branch Naming
| Type | Format | Example |
|------|--------|---------|
| Feature | `feat/description` | `feat/donor-registration` |
| Bug fix | `fix/description` | `fix/notification-crash` |
| Docs | `docs/description` | `docs/update-readme` |
| Chore | `chore/description` | `chore/update-deps` |

## Commit Message Format
Follow [Conventional Commits](https://www.conventionalcommits.org/):
feat: add donor registration form
fix: resolve notification not sending
docs: update architecture diagram
chore: upgrade dependencies

## Pull Request Rules
- Always PR to `dev` branch, never directly to `main`
- At least 1 reviewer must approve before merge
- PR must pass all checks before merge
- Write clear PR description — what changed and why

## Branches
| Branch | Purpose |
|--------|---------|
| `main` | Production — stable release only |
| `dev` | Active development |
| `feat/*` | New features |
| `fix/*` | Bug fixes |

## Code Style
- Use TypeScript strictly — no `any` types
- ESLint + Prettier must pass
- Write meaningful variable and function names
- Add comments for complex logic

## Need Help?
Open an issue or start a discussion — we're friendly here! 😊
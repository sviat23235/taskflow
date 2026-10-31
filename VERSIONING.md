# Політика версіонування

## Семантичне версіонування (SemVer): MAJOR.MINOR.PATCH
| Частина | Коли змінюється | Приклад |
|---|---|---|
| MAJOR | несумісні (зламні) зміни API/даних | 1.4.2 → 2.0.0 |
| MINOR | нова функціональність, сумісна зі старою | 1.0.0 → 1.1.0 |
| PATCH | виправлення помилок без зміни API | 1.1.0 → 1.1.1 |

Передрелізні версії: `1.0.0-rc.1`. Теги мають формат `vMAJOR.MINOR.PATCH`.

## Git-стратегія: спрощений GitFlow
- `main` — лише стабільні релізні версії (кожен коміт позначений тегом);
- `develop` — інтеграція готових фіч;
- `feature/*` — одна гілка на одну фічу, створюється від `develop`;
- `release/*` — підготовка релізу (опційно для малої команди);
- `hotfix/*` — термінові виправлення від `main`, зливаються в `main` і `develop`.

## Угода про коміти (Conventional Commits)
`feat(scope): ...` → MINOR, `fix(scope): ...` → PATCH, `feat!:` або `BREAKING CHANGE:` → MAJOR; також `docs`, `test`, `chore`, `refactor`.

## Процес
1. `git checkout -b feature/<назва> develop`
2. Робота й коміти, `git push origin feature/<назва>`
3. Pull Request + code review
4. `git checkout develop && git merge --no-ff feature/<назва>`
5. Для релізу: merge `develop` → `main`, `git tag -a vX.Y.Z -m "Release X.Y.Z"`, `git push origin vX.Y.Z`
6. Оновити `CHANGELOG.md` і створити release notes за `RELEASE_TEMPLATE.md`

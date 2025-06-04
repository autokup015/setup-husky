# setup-husky

1. Setup husky in project

```shell
pnpm dlx husky-init && pnpm install
```

When install succes you will get husky pre-commit files on .husky

```cmd
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

npm test
```

You can change command when before commit at npm test to other command such as

```shell
npm run lint
```

2. Create husky commit-msg for pattern commit code

```shell
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit'
```

3. Create commitlint.config.js

```shell
pnpm add -D @commitlint/cli @commitlint/config-conventional
```

Create File

```file
commitlint.config.js
```

In file

```ts
export default { extends: ["@commitlint/config-conventional"] };
```

This exp help for before commit that you want to do something such as npm run lint or check error

The pattern code commit every commit should be [build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test]

If commit not match this pattern, this commit is not pass like this

```shell
git commit -m "hey: naja"
```

result

⧗ input: hey: naja
✖ type must be one of [build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test] [type-enum]

✖ found 1 problems, 0 warnings
ⓘ Get help: https://github.com/conventional-changelog/commitlint/#what-is-commitlint

Exp commit

```shell
git commit -m "feat(crud): add function crud on product pages"
```

or

```shell
git commit -m "fix(bug): edit product"
```

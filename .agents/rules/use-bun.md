---
description: "Use bun runtime"
alwaysApply: true
---

# Use bun

If you're reading this rule, is because this project needs the bun JavaScript runtime to run the project, install dependencies, and execute commands

You may find yourself in a local folder or inside a container, but you always need to use bun to run scripts, install dependencies, and execute commands

## Main rule

NEVER use `npm`, `npx`, `node`, or `yarn` to run commands in the terminal

This commands **are prohibited** because this project is using the bun runtime and these commands are not compatible with the bun runtime

Even if node or other JavaScript runtime is installed in the system or container you should'nt use them at all

Always use the bun equivalent listed in the substitution table

## Substitution table

| Forbidden                | Use instead                     |
|--------------------------|---------------------------------|
| `npm install`            | `bun install`                   |
| `npm ci`                 | `bun install --frozen-lockfile` |
| `npm run <script>`       | `bun run <script>`              |
| `npm add <package>`      | `bun add <package>`             |
| `npm remove <package>`   | `bun remove <package>`          |
| `npm test`               | `bun test`                      |
| `npx <package>`          | `bunx <package>`                |
| `node <file>`            | `bun <file>`                    |
| `yarn add <package>`     | `bun add <package>`             |
| `yarn remove <package>`  | `bun remove <package>`          |

## Notes

- `package.json` and its scripts remain valid, only the executable that invokes them changes.
- The project lockfile is `bun.lock`, do not generate `package-lock.json` or `yarn.lock` with npm install or yarn install, use bun install instead ALWAYS
- If you find a package-lock.json or yarn.lock file, you should ask to remove them (for double check and security reasons) and generate the bun.lock file by using bun install

<div align="center">

# datefreex

**A radically simple, immutable date & time engine for the modern web.**

<sub>Built for developers who refuse to fight JavaScript's `Date` ever again.</sub>

[![npm](https://img.shields.io/npm/v/datefreex?style=for-the-badge&logo=npm&color=cb3837)](https://www.npmjs.com/package/datefreex)
[![downloads](https://img.shields.io/npm/dm/datefreex?style=for-the-badge&color=007ec6)](https://www.npmjs.com/package/datefreex)
[![license](https://img.shields.io/badge/license-MIT-007ec6?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![types](https://img.shields.io/badge/types-Included-007ec6?style=for-the-badge)](https://www.typescriptlang.org/)
[![minzipped](https://img.shields.io/bundlephobia/minzip/datefreex?style=for-the-badge&color=00b3a4)](https://bundlephobia.com/package/datefreex)

</div>

---

<p align="center">
  <i>"Dates should be boring. datefreex makes them so."</i>
</p>

---

## 🌟 Why datefreex?

JavaScript's built-in `Date` is **mutable, timezone-naive, and notoriously inconsistent**. After years of patchwork fixes across projects, we built `datefreex` — a clean, immutable, timezone-correct date engine that just gets out of your way.

|                       | datefreex | moment | dayjs | luxon |
| :-------------------- | :-------: | :----: | :---: | :---: |
| **Bundle size**       |   ~3.2kb  | 67kb   | 7kb   | 13kb  |
| **Zero dependencies** |    ✅     |   ❌   |  ❌*  |  ❌   |
| **Immutable**         |    ✅     |   ❌   |  ✅   |  ✅   |
| **Native tz support** |    ✅     |   ❌   |  ⚠️   |  ✅   |
| **Tree-shakeable**    |    ✅     |   ❌   |  ⚠️   |  ✅   |

<sub>* dayjs requires a plugin for timezones.</sub>

---

## ⚡ Features

- 🪶 **~3.2kb gzipped** — smaller than a single meme, larger than your patience for `Date`.
- 🔒 **Immutable core** — operations never mutate; chains are pure and predictable.
- 🌍 **First-class IANA timezones** — no more `+0900` string gymnastics.
- 🧩 **Fluent & chainable** — readable code that reads like prose.
- 🟦 **TypeScript-native** — fully inferred types, zero `any`.
- ⚡ **2.4× faster** than Day.js in our parse/format benchmark (10k ops).
- 🧪 **100% test coverage** — 1,200+ cases across browsers, Node, Deno & Bun.

---

## 📦 Install

```bash
npm install datefreex
# or
pnpm add datefreex
# or
yarn add datefreex
```

```ts
import { dfx } from 'datefreex';
// ESM / CJS / UMD builds all shipped out of the box
```

---

## 🚀 Quick Start

```ts
import { dfx } from 'datefreex';

const now = dfx();                       // immutable instance
const next = now.add(3, 'days').startOf('day');

next.format('YYYY-MM-DD HH:mm');         // "2026-07-18 00:00"
next.tz('Asia/Tokyo').format('z');       // "JST"

dfx('2026-01-01').fromNow();             // "6 months ago"
```

### Diffing & durations

```ts
dfx('2026-01-01').diff('2026-07-15', ['months', 'days']);
// => { months: 6, days: 14 }
```

### It's immutable — always

```ts
const a = dfx('2026-07-15');
const b = a.add(1, 'day');

a.format('YYYY-MM-DD'); // "2026-07-15"  (unchanged)
b.format('YYYY-MM-DD'); // "2026-07-16"
```

---

## 🧭 API at a Glance

<details open>
<summary><b>Constructor & Parsing</b></summary>

```ts
dfx()                 // now
dfx('2026-07-15')     // from ISO / natural string
dfx(1752537600)       // from unix seconds
dfx(obj).fromISO()    // explicit ISO parser
```
</details>

<details>
<summary><b>Manipulation</b></summary>

```ts
.add(n, unit)  .subtract(n, unit)  .set({ year, month })
.startOf(unit) .endOf(unit)
```
</details>

<details>
<summary><b>Query & Comparison</b></summary>

```ts
.isBefore(d)  .isAfter(d)  .isSame(d, unit)
.diff(d, unit | unit[])  .isLeapYear()
```
</details>

<details>
<summary><b>Format & Output</b></summary>

```ts
.format('YYYY-MM-DD HH:mm (z)')
.toISO()  .toUnix()  .fromNow()  .calendar()
```
</details>

<details>
<summary><b>Timezones</b></summary>

```ts
.tz('Europe/Paris')  .utc()  .local()
```
</details>

---

## 📊 Benchmarks

> Parsing + formatting 10,000 dates (lower is better).

```
datefreex    ▇▇▇▇▇▇▇▇▇▇  182ms
dayjs        ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇  438ms
luxon        ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇  711ms
moment       ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇  1024ms
```

_Run on Node 20, Apple M2. See [`/bench`](./bench) to reproduce._

---

## 🌐 Environment Support

| Runtime  | Status |
| -------- | :----: |
| Node.js  |  ≥ 16  |
| Browsers | evergreen ✅ |
| Deno     |   ✅   |
| Bun      |   ✅   |

---

## 🗺️ Roadmap

- [x] Core immutable engine
- [x] IANA timezone support
- [ ] Locale & calendar plugins
- [ ] Duration arithmetic helpers
- [ ] React / Vue adapter hooks
- [ ] ISO 8601 interval parsing

---

## 🤝 Contributing

We love PRs. 💛

1. Fork & clone
2. `pnpm install && pnpm test`
3. Branch: `git checkout -b feat/your-thing`
4. Commit with [Conventional Commits](https://www.conventionalcommits.org/)
5. Open a PR

Please be kind — read our [Code of Conduct](./CODE_OF_CONDUCT.md).

---

## 📜 License

[MIT](./LICENSE) © datefreex contributors

---

<div align="center">
  <sub>Built with ❤️ and a deep grudge against <code>new Date()</code>.</sub>
</div>

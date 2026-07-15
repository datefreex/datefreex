# datefreex

> ⏱️ A modern, zero-dependency date & time toolkit for JavaScript and TypeScript — fast, immutable, and timezone-aware by design.

[![npm version](https://img.shields.io/npm/v/datefreex.svg?style=flat-square)](https://www.npmjs.com/package/datefreex)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![TypeScript](https://img.shields.io/badge/types-Included-blue.svg?style=flat-square)](https://www.typescriptlang.org/)
[![Bundle Size](https://img.shields.io/bundlephobia/min/datefreex?style=flat-square)](https://bundlephobia.com/package/datefreex)

---

## ✨ Why datefreex?

Working with dates in JavaScript is hard. `Date` is mutable, timezone handling is painful, and formatting is inconsistent. **datefreex** rebuilds the experience from the ground up:

- 🪶 **Zero dependencies** — ships a tiny, tree-shakeable bundle
- 🔒 **Immutable** — every operation returns a new instance, no surprises
- 🌍 **Timezone-aware** — first-class IANA timezone support
- 🧩 **Chainable & fluent** — readable, expressive API
- 🟦 **TypeScript-first** — fully typed, with inferred return types
- ⚡ **Fast** — benchmarked against the leading alternatives

---

## 📦 Installation

```bash
# npm
npm install datefreex

# pnpm
pnpm add datefreex

# yarn
yarn add datefreex
```

```ts
import { datefreex } from 'datefreex';
// or CommonJS
const { datefreex } = require('datefreex');
```

---

## 🚀 Quick Start

```ts
import { datefreex } from 'datefreex';

// Create from a local date
const now = datefreex();

// Chain transformations
const nextWeek = now.add(7, 'days').startOf('week');

// Format with intuitive tokens
nextWeek.format('YYYY-MM-DD HH:mm'); // "2026-07-22 00:00"

// Timezone conversion
const tokyo = now.tz('Asia/Tokyo');
tokyo.format('YYYY-MM-DD HH:mm (z)'); // "2026-07-15 17:30 (JST)"

// Human-friendly relative time
datefreex('2026-01-01').fromNow(); // "6 months ago"
```

---

## 📖 API Overview

| Category        | Methods                                                            |
| --------------- | ----------------------------------------------------------------- |
| **Create**      | `datefreex()`, `fromISO()`, `fromUnix()`                          |
| **Manipulate**  | `add()`, `subtract()`, `set()`, `startOf()`, `endOf()`            |
| **Query**       | `isBefore()`, `isAfter()`, `isSame()`, `diff()`                   |
| **Format**      | `format()`, `toISO()`, `toUnix()`, `fromNow()`, `calendar()`      |
| **Timezone**    | `tz()`, `utc()`, `local()`                                        |

> 📚 Full documentation and live examples: **[datefreex.dev](https://datefreex.dev)** _(coming soon)_

---

## 🧪 Examples

### Diffing two dates

```ts
const a = datefreex('2026-01-01');
const b = datefreex('2026-07-15');

a.diff(b, 'months'); // -6
a.diff(b, ['years', 'months', 'days']);
// { years: 0, months: 6, days: 14 }
```

### Immutable by default

```ts
const base = datefreex('2026-07-15');
const moved = base.add(1, 'day');

base.format('YYYY-MM-DD'); // "2026-07-15" — unchanged
moved.format('YYYY-MM-DD'); // "2026-07-16"
```

---

## ⚙️ Compatibility

| Environment | Support          |
| ----------- | ---------------- |
| Node.js     | ≥ 16             |
| Browsers    | Modern evergreen |
| Deno        | ✅               |
| Bun         | ✅               |

---

## 🤝 Contributing

Contributions are welcome! 🎉

1. Fork the repository
2. Create your feature branch (`git checkout -b feat/amazing`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feat/amazing`)
5. Open a Pull Request

Please read our [Code of Conduct](./CODE_OF_CONDUCT.md) before contributing.

---

## 🗺️ Roadmap

- [ ] Plugin system for locales & calendars
- [ ] Duration arithmetic helpers
- [ ] React / Vue binding hooks
- [ ] ISO 8601 interval parsing

---

## 📄 License

Released under the [MIT License](./LICENSE).

<p align="center">Built with ❤️ for developers who are tired of fighting <code>Date</code>.</p>

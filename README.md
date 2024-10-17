<div align="center">
  <picture style="display: flex; flex-direction: column; align-items: center;">
    <source src="./static/addon-example.avif" type="image/avif" />
    <img style="border-radius: 1rem;"
      src="./static/addon-example.png"
      alt="Example of the addon in use, showing badges next to component entries in the sidebar."
      loading="lazy"
      decoding="async"
      height="247"
    />
  </picture>

  <h1>Storybook Addon - Tag Badges</h1>
  
  <p>
    This addon displays badges in the <a href="https://storybook.js.org/docs/configure/user-interface/sidebar-and-urls">sidebar</a> and <a href="https://storybook.js.org/docs/essentials/toolbars-and-globals">toolbar</a> of the Storybook UI, next to <code>component</code>, <code>docs</code> or <code>story</code> entries, based on the <a href="https://storybook.js.org/docs/writing-stories/tags">tags</a> defined in your content. Badges can be customised to support your team's workflows.
  </p>
  
  <p>
    <img src="https://img.shields.io/badge/status-stable-4cc71e" alt="Status: Stable" />
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/commits"><img src="https://img.shields.io/github/commit-activity/m/Sidnioulz/storybook-addon-tag-badges" alt="commit activity" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/commits"><img src="https://img.shields.io/github/last-commit/Sidnioulz/storybook-addon-tag-badges" alt="last commit" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/issues/"><img src="https://img.shields.io/github/issues/Sidnioulz/storybook-addon-tag-badges" alt="open issues" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/actions/workflows/github-code-scanning/codeql"><img src="https://github.com/Sidnioulz/storybook-addon-tag-badges/actions/workflows/github-code-scanning/codeql/badge.svg?branch=main" alt="CodeQL status" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/actions/workflows/continuous-integration.yml"><img src="https://github.com/Sidnioulz/storybook-addon-tag-badges/actions/workflows/continuous-integration.yml/badge.svg?branch=main" alt="CI status" /></a>
    <a href="https://codecov.io/gh/Sidnioulz/storybook-addon-tag-badges"><img src="https://codecov.io/gh/Sidnioulz/storybook-addon-tag-badges/graph/badge.svg?token=4SX3N57XH3" alt="code coverage" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/graphs/contributors"><img src="https://img.shields.io/github/contributors/Sidnioulz/storybook-addon-tag-badges" alt="contributors" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/blob/main/CODE_OF_CONDUCT.md"><img src="https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg" alt="code of conduct: contributor covenant 2.1" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/blob/main/LICENSE"><img src="https://img.shields.io/github/license/Sidnioulz/storybook-addon-tag-badges.svg" alt="license" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/network/members"><img src="https://img.shields.io/github/forks/Sidnioulz/storybook-addon-tag-badges" alt="forks" /></a>
    <a href="https://github.com/Sidnioulz/storybook-addon-tag-badges/stargazers"><img src="https://img.shields.io/github/stars/Sidnioulz/storybook-addon-tag-badges" alt="stars" /></a>
    <a href="https://github.com/sponsors/Sidnioulz"><img src="https://img.shields.io/badge/sponsor-30363D?logo=GitHub-Sponsors&logoColor=#EA4AAA" alt="sponsor this project" /></a>
  </p>
</div>

---

## 📔 Table of Contents

<!-- no toc -->

- [Table of Contents](#-table-of-contents)
- [Which badge addon should I use?](#-which-badge-addon-should-i-use)
- [Installation](#-installation)
- [Default Config](#-default-config)
- [Usage](#-usage)
- [Customise Badge Config](#️-customise-badge-config)
- [Limitations](#-limitations)
- [Contributing](#-contributing)
- [Support](#-support)
- [Contact](#️-contact)
- [Acknowledgments](#-acknowledgments)

## 🤔 Which badge addon should I use?

A few other projects have been written to display badges in Storybook. This addon is a rewrite of [storybook-addon-badges](https://storybook.js.org/addons/@geometricpanda/storybook-addon-badges) from [Jim Drury](https://github.com/geometricpanda), focused on exploiting Storybook [tags](https://storybook.js.org/docs/writing-stories/tags). We use tags as a data source to display badges, rather than dedicated [story parameters](https://storybook.js.org/docs/writing-stories/parameters), as tags are becoming more prevalent in Storybook and have a strong role overlap with badges.

This architectural choice opens up new possibilities, but also prevents some features from the original addon from working. The table below summarises the differences between both addons.

|                             | storybook-addon-tag-badges | [storybook-addon-badges](https://storybook.js.org/addons/@geometricpanda/storybook-addon-badges) |
| --------------------------: | -------------------------- | ------------------------------------------------------------------------------------------------ |
|      Show badges in toolbar | ✅                         | ✅                                                                                               |
|      Show badges in sidebar | ✅                         | ⚠️ _only for current story_                                                                      |
| Define badges based on tags | ✅                         | ❌                                                                                               |
|     Per-story customisation | ❌                         | ✅                                                                                               |
|             Tooltip support | ⚠️ _only in toolbar_       | ✅                                                                                               |
|            Storybook >= 8.4 | ✅                         | ✅                                                                                               |
|             Storybook < 8.3 | ❌                         | ✅                                                                                               |

## 📦 Installation

```sh
yarn add -D storybook-addon-tag-badges
```

```sh
npm install -D storybook-addon-tag-badges
```

```sh
pnpm install -D storybook-addon-tag-badges
```

In your `.storybook/main.ts` file, add the following:

```ts
export default {
  addons: ['storybook-addon-tag-badges'],
}
```

## 🏁 Default Config

This addon comes with a default config, allowing you to get started immediately by adding tags to your content.

### Preconfigured Badges

|                            Preview | Tag patterns                          | Suggested use                                                                                                      |
| ---------------------------------: | ------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
|        ![](./static/badge-new.png) | `new`                                 | Recently added components or props/features                                                                        |
|       ![](./static/badge-beta.png) | `alpha`, `beta`, `rc`, `experimental` | Warn that a component or prop is not stable yet                                                                    |
| ![](./static/badge-deprecated.png) | `deprecated`                          | Components or props that should be avoided in new code                                                             |
|   ![](./static/badge-outdated.png) | `outdated`                            | Components with design changes that weren't yet implemented, which can incur extra development costs to your users |
|     ![](./static/badge-danger.png) | `danger`                              | Components that require particular attention when configuring them (e.g. for with security concerns)               |
|  ![](./static/badge-code-only.png) | `code-only`                           | Components that only exist in code, and not in design                                                              |
|    ![](./static/badge-version.png) | `version:*`                           | Per-component versioning                                                                                           |

### Display Logic

By default, all tags are always displayed on the toolbar, but they're only displayed for component entries in the sidebar.

Besides, the addon is limited to one badge per entry in the sidebar. Badges placed first in the configuration will be displayed in priority. For example, the `new` badge will be displayed before the `code-only` badge.

## 👀 Usage

To display preconfigured badges, add the relevant tags to your components, stories, or docs entries.

### Component Badges

To set badges for a component (and its child stories), define `tags` in the component's meta:

```ts
// src/components/Button.stories.ts
import type { Meta, StoryObj } from '@storybook/react'
import { Button } from './Button'

const meta: Meta<typeof Button> = {
  title: 'Example/Button',
  component: Button,
  tags: ['autodocs', 'version:1.0.0', 'new'],
}
```

### Story Badges

To add badges to a specific story, add `tags` to the story object itself:

```ts
// src/components/Button.stories.ts
export const Tertiary: StoryObj<typeof Button> = {
  args: {
    variant: 'tertiary',
    size: 'md',
  },
  tags: ['experimental'],
}
```

### Docs Badges

To set badges for a docs entry, pass a `tags` array to the [`docs` parameter](https://storybook.js.org/docs/writing-stories/parameters):

```ts
// src/components/Button.stories.ts
import type { Meta, StoryObj } from '@storybook/react'
import { Button } from './Button'

const meta: Meta<typeof Button> = {
  title: 'Example/Button',
  component: Button,
  parameters: {
    docs: {
      tags: ['outdated'],
    },
  },
}
```

## 🛠️ Customise Badge Config

In your manager file, you may redefine the config object used to map tags to badges. Each tag is only rendered once, with the first badge configuration it matches; therefore, make sure to place your overrides to the config first if you also want to keep the default config in place.

```ts
// .storybook/manager.ts
import { addons } from '@storybook/manager-api'
import {
  defaultConfig,
  type TagBadgeParameters,
} from 'storybook-addon-tag-badges'

addons.setConfig({
  tagBadges: [
    {
      tags: 'frog',
      badge: {
        text: 'Frog 🐸',
        bgColor: '#001c13',
        fgColor: '#e0eb0b',
        tooltip: 'This component can catch flies!',
      },
      display: {
        sidebar: ['component'],
        toolbar: true,
      },
    },
    // Place the default config after your custom matchers.
    ...defaultConfig,
  ] satisfies TagBadgeParameters,
})
```

---

---

---

---

---

---

---

### Display

The `display` property in the badge configuration controls where and for what type of content the badges are rendered. It has two sub-properties:

- `sidebar`: Controls the display of badges in the sidebar.
- `toolbar`: Controls the display of badges in the toolbar.

Each of these can be set to:

- `true`: Displays for any type of item.
- `false`: Never displays.
- A string or array of strings: Each string represents a type of HashEntry for which the badge will be shown (e.g., 'docs', 'story', 'component').

Example:

```ts
// .storybook/manager.ts
import { addons } from '@storybook/manager-api'
import {
  defaultConfig,
  type TagBadgeParameters,
} from 'storybook-addon-tag-badges'

addons.setConfig({
  tagBadges: [
    {
      tags: 'custom-badge',
      badge: {
        text: 'Custom',
        bgColor: '#ff0000',
        fgColor: '#ffffff',
      },
      display: {
        sidebar: ['component', 'story'],
        toolbar: true,
      },
    },
    ...defaultConfig,
  ] satisfies TagBadgeParameters,
})
```

This configuration would display the 'Custom' badge in the sidebar for components and stories, and in the toolbar for all types of content when the 'custom-badge' tag is present.

### Tag

The `tags` property in the badge configuration defines the string, RegExp, or tag structures to match against for this badge config to be used. It can be a single pattern or an array of patterns.

A tag pattern can be:

- A string: Exact match for the tag.
- A RegExp: For more complex matching patterns.
- An object with `prefix` and/or `suffix` properties: To match only the beginning or end of a tag.

Examples:

```ts
// .storybook/manager.ts
import { addons } from '@storybook/manager-api'
import {
  defaultConfig,
  type TagBadgeParameters,
} from 'storybook-addon-tag-badges'

addons.setConfig({
  tagBadges: [
    // String match
    {
      tags: 'new-feature',
      badge: { text: 'New Feature' },
    },
    // RegExp match
    {
      tags: /^version:\d+\.\d+\.\d+$/,
      badge: ({ tag }) => ({ text: tag.split(':')[1] }),
    },
    // Prefix/suffix match
    {
      tags: { prefix: 'status:' },
      badge: ({ tag }) => ({ text: tag.split(':')[1] }),
    },
    // Array of patterns
    {
      tags: ['beta', { suffix: '-test' }, /^v\d+/],
      badge: { text: 'Testing', bgColor: '#ffff00' },
    },
    ...defaultConfig,
  ] satisfies TagBadgeParameters,
})
```

### Badge

The `badge` property defines the appearance and content of the badge to display. It can be either a static object or a function that dynamically generates the badge based on the matched content and tag.

Static badge object:

```ts
// .storybook/manager.ts
import { addons } from '@storybook/manager-api'
import {
  defaultConfig,
  type TagBadgeParameters,
} from 'storybook-addon-tag-badges'

addons.setConfig({
  tagBadges: [
    {
      tags: 'important',
      badge: {
        text: 'Important',
        bgColor: '#ff0000',
        fgColor: '#ffffff',
        borderColor: '#000000',
        tooltip: 'This is an important component',
      },
    },
    ...defaultConfig,
  ] satisfies TagBadgeParameters,
})
```

#### Dynamic Badge Functions

Dynamic badge functions allow you to customize the badge based on the current entry and matched tag. This is particularly useful for creating badges that adapt to specific tag content or entry properties.

The function receives an object with the following properties:

- `entry`: The current HashEntry (component, story, etc.).
- `getTagParts`, `getTagPrefix`, `getTagSuffix`: Utility functions to extract parts of the tag.
- `tag`: The matched tag string.

Example of a dynamic badge function:

```ts
// .storybook/manager.ts
import { addons } from '@storybook/manager-api'
import {
  defaultConfig,
  type TagBadgeParameters,
} from 'storybook-addon-tag-badges'

addons.setConfig({
  tagBadges: [
    {
      tags: /^version:/,
      badge: ({ entry, getTagSuffix, tag }) => {
        const version = getTagSuffix(tag, 'version:')
        return {
          text: `v${version}`,
          bgColor: entry.type === 'story' ? '#e0f0ff' : '#f0e0ff',
          tooltip: `Version ${version} - ${entry.name}`,
        }
      },
    },
    ...defaultConfig,
  ] satisfies TagBadgeParameters,
})
```

This function creates a version badge that changes color based on whether it's applied to a story or another type of entry, and includes the entry name in the tooltip.

---

---

---

---

---

---

---

## 🐌 Limitations

### Per-Story Config

This addon does not support changing the badge config for a specific story, and never will. This is because parts of the Storybook UI, like the sidebar, are rendered in a context where story data is not loaded. Storybook has stopped preloading all story data in v7, to improve performance.

As a result, we need to create sidebar tags without access to story-specific data. This addon uses the [core addon API](https://storybook.js.org/docs/addons/addons-api#core-addon-api) to read your configuration, and so the way to customise the rendering of a specific badge is to use [dynamic badge functions](<(#dynamic-badge-functions)>). Those functions can exploit a story's ID, title, or tag content to customise the rendered badge, as examples below will show.

### Component tags

In Storybook, your MDX and CSF files are converted to `docs`, `component`, `group` and `story` entries to render the sidebar, each with their own semantics. `docs` and `story` entries directly inherit the tags defined in `parameters.docs.tags` and in the [CSF `meta`](https://storybook.js.org/docs/api/csf#default-export), respectively.

For `component` entries, tags are computed indirectly: they are the intersection of tags present on all of the component's stories. For example, for a component that defines the tag `version:1.2.0` in its `meta`, and has one story that defines an additional tag `deprecated`, the component entry will only have the `version:1.2.0` tag defined.

In particular, if a component `meta` defines two tags `outdated` and `version:1.1.0`, but one story explicitly removes the tag `outdated` (by adding `!outdated`), then the component entry will only have tag `version:1.1.0`.

## 👩🏽‍💻 Contributing

### Code of Conduct

Please read the [Code of Conduct](https://github.com/Sidnioulz/storybook-addon-tag-badges/blob/main/CODE_OF_CONDUCT.md) first.

### Developer Certificate of Origin

To ensure that contributors are legally allowed to share the content they contribute under the license terms of this project, contributors must adhere to the [Developer Certificate of Origin](https://developercertificate.org/) (DCO). All contributions made must be signed to satisfy the DCO. This is handled by a Pull Request check.

> By signing your commits, you attest to the following:
>
> 1. The contribution was created in whole or in part by you and you have the right to submit it under the open source license indicated in the file; or
> 2. The contribution is based upon previous work that, to the best of your knowledge, is covered under an appropriate open source license and you have the right under that license to submit that work with modifications, whether created in whole or in part by you, under the same open source license (unless you are permitted to submit under a different license), as indicated in the file; or
> 3. The contribution was provided directly to you by some other person who certified 1., 2. or 3. and you have not modified it.
> 4. You understand and agree that this project and the contribution are public and that a record of the contribution (including all personal information you submit with it, including your sign-off) is maintained indefinitely and may be redistributed consistent with this project or the open source license(s) involved.

### Getting Started

This project uses PNPM as a package manager, and Turbo as a monorepo provider.

- See the [installation instructions for PNPM](https://pnpm.io/installation)
- Run `pnpm i`

### Useful commands

- `pnpm start` starts the local Storybook
- `pnpm build` builds and packages the addon code
- `pnpm pack:local` makes a local tarball to be used as a NPM dependency elsewhere
- `pnpm test` runs unit tests

### Migrating to a later Storybook version

If you want to migrate the addon to support the latest version of Storyboook, you can check out the [addon migration guide](https://storybook.js.org/docs/addons/addon-migration-guide).

### Release System

> [!CAUTION]
> TODO

## 🆘 Support

Please [open an issue](https://github.com/Sidnioulz/storybook-addon-tag-badges/issues/new) for bug reports or code suggestions. Make sure to include a working Minimal Working Example for bug reports. You may use [storybook.new](https://new-storybook.netlify.app/) to bootstrap a reproduction environment.

## ✉️ Contact

Steve Dodier-Lazaro · `@Frog` on the [Storybook Discord](https://discord.gg/storybook) - [LinkedIn](https://www.linkedin.com/in/stevedodierlazaro/)

Project Link: [https://github.com/Sidnioulz/storybook-addon-tag-badges](https://github.com/Sidnioulz/storybook-addon-tag-badges)

## 💛 Acknowledgments

### Thanks

- [Jim Drury](https://github.com/geometricpanda) for his groundbreaking working on the original Badges Addon; I am a mere copy-cat
- [Michael Shilman](https://github.com/shilman) for his help with addon internals and his feedback
- All the contributors to the [Storybook addon kit](https://github.com/storybookjs/addon-kit)

### Built With

[![Dependabot](https://img.shields.io/badge/Dependabot-025E8C?logo=dependabot&logoColor=white)](https://github.com/dependabot)
[![ESLint](https://img.shields.io/badge/ESLint-4b32c3?logo=eslint&logoColor=white)](https://eslint.org/)
[![GitHub](https://img.shields.io/badge/GitHub-0d1117?logo=github&logoColor=white)](https://github.com/solutions/ci-cd)
[![Prettier](https://img.shields.io/badge/Prettier-f8bc45?logo=prettier&logoColor=black)](https://prettier.io/)
[![Storybook](https://cdn.jsdelivr.net/gh/storybookjs/brand@main/badge/badge-storybook.svg)](https://storybook.js.org/)
[![tsup](https://img.shields.io/badge/tsup-fde047)](https://tsup.egoist.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178c6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vitest](https://img.shields.io/badge/Vitest-acd268?logo=vitest&logoColor=black)](https://https://vitest.dev/)

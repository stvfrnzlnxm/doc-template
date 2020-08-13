# Project Name

**This is the description of the project. It is clear, short, and to the point. It describes the importance of the project, and what it does. Extra points for listing all technologies and tools used in this project, e.g.:**

- [Next.js](nextjs.org/)
- [Prismic](prismic.io/)
- [Storybook](storybook.js.org/)
- [TypeScript](typescriptlang.org/)
- [styled-components](https://styled-components.com/)

## Table of Contents 🔍

1. [Installation](#1.-installation-🛠)
2. [Usage](#2.-usage-💻)
3. [Cheat Sheet](#3.-cheat-sheet-🙇‍♂️)

## 1. Installation 🛠

**This section will tell the user how to install the project locally.**

Execute `yarn install` to install all necessary dependencies. Get the latest version of Yarn here: [yarnpkg.com](https://yarnpkg.com/).

For working mock up data copy `api/prismic/config/configuration-dummy.ts`, rename it to `api/prismic/config/configuration.js` and edit the variables.

## 2. Usage 💻

**In this section you instruct other people on how to use your project after they’ve installed it.**

### 2.1 Development

Execute `yarn dev` to start the development server. `**/**/test` folders contain snapshots and unit tests.

### 2.2 Testing

Execute `yarn test:all` to run all test scripts. Note that there is a pre-push hook that runs `yarn test:all`.

### 2.3 Build

To run the build version of the project, execute `yarn build`.

### 2.4 Prismic

This setup requires the following custom types:

- homepage
- page
- global_config

Add new slices (prismic modules) inside `api/prismic/slices/map.ts`.

To render slices according to `api/prismic/slices/map.ts.`, use `src/templates/partials/ComponentsRenderer.tsx` like so:

```javascript
<ComponentsRenderer slices={get(data, 'data.body', [])} />
```

Modify `api/prismic/helper/richtextHtmlSerializer.ts` to impact editors richtext input, wich is handled by the Prismic rich text resolver.

It is recommended to use `src/helpers/preventScriptInjection.ts` if the editor has a possibility to insert script inside the Prismic rich text editor.

### 2.5 Languages

Edit languages inside `server/server.ts`.

## 3. Cheat Sheet 🙇‍♂️

Handling prismic rich texts:

```javascript
import { RichText } from 'prismic-reactjs';

const richtText = RichText.render(
  prismic.richtext.object,
  linkResolver,
  htmlSerializer
);
```

Get current breakpoint:

```javascript
const breakpoint = useContext(BreakpointContext);
```

Access theme (variables):

```javascript
const theme = useContext(ThemeContext);
```

Access data from prismic's global_conf:

```javascript
const globalData = useContext(GlobalConfigContext);
```

Use `src/components/atoms/NextLink/NextLink.tsx` for internal and external link handling. Links inside a richt text are handled the similar way.

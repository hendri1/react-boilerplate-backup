## Style Guides

This document contains style guides, components usage, pattern used on react-boilerplate

## Table of contents
  - [Syntax](#syntax)
    - [HTML and CSS](#html-and-css)
    - [Javascript](#javascript)
    - [React](#react)
  - [Pattern](#pattern)
    - [Atomic Design](#atomic-design)
    - [Project Structure](#project-structure)
  - [Naming Convension](#naming-convension)
    - [Commits](#commits)
    - [Component](#component)
  - [Variable](#variable)
  - [Ordered Import](#ordered-import)
    - [Expand the Ordered Import](#expand-the-ordered-import)
  - [Using Arrow Functional](#using-arrow-functional)
  - [Responsive](#responsive)

## Syntax
### HTML and CSS
Please read [Code Guide](https://codeguide.co/) for Standards development consistent, flexible, and sustainable HTML and CSS

### Javascript
Please read [Standard JS](https://standardjs.com/) style guide for JS code with some modified rules. Modified rules can be seen on `.eslintrc.js`

### React
Please read [React Standard Style Guide](https://github.com/standard/eslint-config-standard-react). Modified rules can be seen on `.eslintrc.js`

## Pattern
### Atomic Design
Please read [Atomic Design](http://bradfrost.com/blog/post/atomic-web-design/) for designing reusable components

| Name | Description |
|------|-------------|
| `atoms` | atoms are the smallest possible components, such as buttons, titles, inputs. They can be applied on any context, globally or within other components and templates |
| `molecules` | they are the composition of one or more components of atoms. Here we begin to compose complex components and reuse some of those components. Molecules can have their own properties and create functionalities by using atoms, which don’t have any function or action by themselves |
| `organisms` | organisms are the combination of molecules that work together or even with atoms that compose more elaborate interfaces. At this level, the components begin to have the final shape, but they are still ensured to be independent, portable and reusable enough to be reusable in any content |
| `templates` | in this state we stop composing components and begin to set their context. Moreover, the templates create relationships between the organisms and others components through positions, placements and patterns of the pages but it doesn’t have any style, color or component rendered. That’s why it looks like a wireframe |
| `pages` | pages are the navigate parts of the application and it’s where the components are distributed in one specific template |

> **Notes :** <br> 
> don't make all the folders above, and make sure to create a folder that you only need

### Project Structure

| Name | Description |
|------|-------------|
| `asstes` | contains all assets like images, fonts, and css |
| `components` | contains unique component that only used in `pages` |
| `configs` | contains all logic for integrate with API |
| `contexts` | contains react context for store data that can be global mutable |
| `lang` | contains various languages for each `pages` |
| `libraries` | contains all libraries that used |
| `pages` | contains all view of application |
| `providers` | contains all providers for mutate `contexts` |
| `routes` | contains all routes that used |
| `services` | contains all services for mutate `contexts` and call API |
| `utils` | contains all utilization for help an action |

## Naming Convension
### Commits
One of our pain is writing the changelogs for each release, that why we use [Conventional Commits](https://www.conventionalcommits.org/) to reduce the pain

| Name | Description |
|-----|-------|
| `feat` | a new feature  |
| `fix` | a bug fix   |
| `improvement` | an improvement to a current feature |
| `docs` | documentation only changes  |
| `style` | changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc) |
| `refactor` | a code change that neither fixes a bug nor adds a feature  |
| `perf` | a code change that improves performance |
| `test` | adding missing tests or correcting existing tests  |
| `build` | changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)  |
| `ci` | changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs) |
| `chore` | other changes that don't modify src or test files |
| `revert` | reverts a previous commit  |

This way, we can automatically generate changelogs for each releases which decreases our release process time

### Component
We use `PascalCase` for naming Components

> Components

```
components/
└── atoms/
    └── TcButton/
        └── index.js
```
<br>

## Variable
Make sure to use `camelCase` for naming javascript variable, because we don't set `camelCase` rules to `err` in `.eslintrc`

Why?

Because in the back end, we don't use `camelCase` but `snake_case`, that why sometimes we must be used `snake_case` for naming javascript variable if the API that we using have a parameters

**Example :**

```
http://${REACT_APP_API_URL}/api/v1/users/all?per_page=5&current_page=1&type=user
```

## Function
Make sure to use `camelCase` for naming javascript function and add suffix `handle`

**Example :**

``` javascript
const handleSubmit = () => {
  // your action
}
```

## Ordered Import
A guide for ordered import

``` javascript
// dependencies
import React, { useState, useEffect } from 'react'
import { useForm } from 'react-hook-form'
import styled from 'styled-components'

// libraries
import { useTranslation } from 'libraries'

// services
import { AuthService, JobService } from 'services'

// contexts
import { AuthContext } from 'contexts'

// utils
import { handleAsync } from 'utils'

// utils
import { 
  addIcon,
  removeIcon,
  errorIcon
} from 'assets'

// components
import {
  // atoms
  TcButton,

  // molecules
  TcTabs,

  // organisms
  TcForm,

  // templates
  TcBlankTemplate
} from 'components'
```

> **Notes :** <br> 
> Make sure to import a components that you only need

### Expand the Ordered Import
If you import more than 3 components, make sure to expanded

``` javascript
// bad
import { addIcon, removeIcon, errorIcon, searchIcon } from 'assets'

// good
import { 
  addIcon,
  removeIcon,
  errorIcon,
  searchIcon
} from 'assets'
```

> **Notes :** <br> 
> Make sure to import a components that you only need

## Using Arrow Functional
### Page
``` jsx
import React, { useState, useEffect } from 'react'

const [yourState, setYourState] = useState(false)

const Page = () => {

  const handleChangeState = (value) => {
    setYourState(value)
  }

  return (
    <>
      <p>{yourState}</p>
      <button onClick={() => handleChangeState('aha')}>Change</button>
    </>
  )
}

export default Page
``` 

### Component
``` jsx
import React, { memo } from 'react'
import PropTypes from 'prop-types'

const TcIconClass = `
  tw-inline-block
`

const TcIcon = memo((props) => {
  const { src, alt, width, className } = props

  return (
    <img
      src={src}
      alt={alt}
      className={TcIconClass + className}
      width={width}
    />
  )
})

TcIcon.propTypes = {
  src: PropTypes.string.isRequired,
  alt: PropTypes.string.isRequired,
  width: PropTypes.string,
  className: PropTypes.string
}

TcIcon.defaultProps = {
  width: '20px',
  className: ''
}

export default TcIcon
```

## Responsive
You can use the `breakpoints` function that we create if you don't find a [CSS utility](https://v0.tailwindcss.com/docs/what-is-tailwind/) on the screen size that you need or your CSS looks strange at a certain screen size

| Size | Pixel |
|------|-------|
| `xs` | 576 |
| `sm` | 768 |
| `md` | 992 |
| `lg` | 1200 |
| `xl` | 1920 |

<br>

| Option | Pixel | Description |
|--------|-------|-------------|
| `default` | ≥ `size` and < `size` | `min-width` and `max-width` |
| `min` | ≥ `size` | `min-width` |
| `max` | < `size` | `max-width` |

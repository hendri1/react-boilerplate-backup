## Contribution 
A guide to contributing to this repository before you make other amazing features

## Table of contents
  - [Requirement](#Requirement)
  - [First touch](#First-touch)
  - [Before write code](#Before-write-code)
  - [How to start](#How-to-start)
  - [Check your code with Production Environment](#Check-your-code-with-Production-Environment)

### Requirement
* Node JS (v12.x.x or latest)
* Yarn

### First touch
Clone from project repository 

```
$ git clone https://github.com/hendri1/react-boilerplate.git
```

Create your amazing features branch based on `master` branch

``` bash
$ git checkout -b your_branch_name
```

See [gitflow](git-flow.md)

### Before write code
Copy `.env.example` to `.env` and suitable with your [environment](environment.md)

``` bash
$ cp .env.example .env
```

### How to start

``` bash
# install dependencies
$ yarn

# serve with hot reload. default run at localhost:3000
$ yarn start
```

### Check your code with Production Environment

``` bash
# build for production and launch server
$ yarn build
```

See [all command](command.md)

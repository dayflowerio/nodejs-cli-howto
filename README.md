# nodejs-cli-howto
Docs for creating an NPM distributable Node.js CLI following best practices

## Requirements
- nvm
- gh - Github CLI
- yarn


## Initializing repo

1. Setup repo and basic folder structure.
```
$ nvm install --lts
$ nvm use --lts
$ gh repo new
$ cd name-of-new-repo
$ mkdir bin
$ mkdir -p src/lib/commands
$ cat "#!/usr/bin/env node" > ./bin/cli.js
$ touch src/command.js
$ yarn init
$ yarn add -D semver
$ yarn add @inquirer/prompts chalk commander dotenv ora configstore
```

2. Add `bin` clause to package.json
```
...
  "bin" {
    "command-name": "./bin/cli.js"
  },
...
```

## Folder structure
```
.env
.gitignore
README.md
bin/
  cli.js
package.json
sample.env
src/
  command.js
  lib/
    commands/
yarn.lock
```


## Resources
- https://dev.to/boudydegeer/mastering-nodejs-cli-best-practices-and-tips-7j5
  - Respect POSIX arguments like -v
  - Build empathetic CLIs with helpful messages
  - Stateful data managment using `configstore`
  - Use `Chalk` for colorful experience
  - Enhance interactivity with `inquirer`
  - Use hyperlinks in messages with relevant links
  - Zero configuration initial setup
  - Respect POSIX signals like `SIGINT`
- https://www.sitepoint.com/javascript-command-line-interface-cli-node-js/
- https://www.twilio.com/en-us/blog/how-to-build-a-cli-with-node-js
- https://webbylab.com/blog/best-practices-for-building-cli-and-publishing-it-to-npm/

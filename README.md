# Node.js CLI HOWTO
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
$ mkdir -p src/lib
$ mkdir -p src/commands
$ cat "#!/usr/bin/env node\n\nprocess.on('SIGINT', () => {\n  console.log('Process interrupted. Exiting gracefully.')\n  process.exit(0)\n})\n" > ./bin/cli.js
$ chmod a+x ./bin/cli.js
$ touch src/command.js
$ yarn init
$ yarn add -D semver
$ yarn add @inquirer/prompts chalk commander dotenv ora configstore
$ yarn add .
$ yarn commit -m 'added CLI scaffolding'
$ yarn link
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

## Useful packages
- [semver](https://github.com/npm/node-semver) - Semantic version management
- inquirer - CLI interactivity
- [chalk](https://github.com/chalk/chalk) - CLI terminal colorization
- [commander](https://github.com/tj/commander.js) - CLI framework
- dotenv - Read .env files
- ora - CLI terminal loading indicators
- configstore - Configuration state management


## Resources
- https://github.com/lirantal/nodejs-cli-apps-best-practices?tab=readme-ov-file#41-containerize-the-cli
- https://dev.to/boudydegeer/mastering-nodejs-cli-best-practices-and-tips-7j5
  - Respect POSIX arguments like -v
  - Build empathetic CLIs with helpful messages
  - Stateful data managment using `configstore`
  - Use `Chalk` for colorful experience
  - Enhance interactivity with `inquirer`
  - Use hyperlinks in messages with relevant links
  - Zero configuration initial setup
  - Respect POSIX signals like `SIGINT`
- https://medium.com/nmc-techblog/building-a-cli-with-node-js-in-2024-c278802a3ef5
- https://www.freecodecamp.org/news/nodejs-tutorial-build-a-task-manager-cli-tool/
- https://byby.dev/node-command-line-libraries
- https://www.sitepoint.com/javascript-command-line-interface-cli-node-js/
- https://www.twilio.com/en-us/blog/how-to-build-a-cli-with-node-js
- https://webbylab.com/blog/best-practices-for-building-cli-and-publishing-it-to-npm/
- https://medium.com/netscape/a-guide-to-create-a-nodejs-command-line-package-c2166ad0452e
- https://2ality.com/2022/08/installing-nodejs-bin-scripts.html
- https://swizec.com/blog/making-a-node-cli-both-global-and-local/
- https://nodejs.org/en/learn/command-line/run-nodejs-scripts-from-the-command-line
- https://docs.npmjs.com/cli/v10/configuring-npm/package-json
- 



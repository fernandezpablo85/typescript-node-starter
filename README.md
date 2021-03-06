TypeScript node app starter
===========================

This is a starter project that will let you write node apps written in TypeScript in no time.

Usage:
------

To start using the `typescript node starter` you just need to follow this steps

```bash
# clone this repo (change myapp for your application name)
$ git clone git@github.com:acamica/typescript-node-starter.git myapp
$ cd myapp
# Install your deps using yarn or npm and follow the questions.
$ npm install
```


Features
--------
* TypeScript Workflow
* Unit testing and tdd/bdd workflow
* TSlint before commit
* GIT messages validator using format like `feat(general): Some description`
* Reliable package management using [yarn](https://yarnpkg.com/en/)
* Homogeneous service environment using [Docker](https://www.docker.com/)
* Visual Studio Code configuration
* [Editor config](http://editorconfig.org/) for editors that supports it like Visual Code

### TypeScript Workflow
TypeScript v2.3

TODO: explain `npm start` and `npm run build-and:start`

TODO: explain strict rules

        "noImplicitAny": true,
        "noImplicitThis": true,
        "noUnusedLocals": true,
        "noImplicitReturns": true,
        "noFallthroughCasesInSwitch": true,
        "strictNullChecks": true,

### Unit testing & TDD

Unit testing is your first line of defense against bugs when you are developing your application, but it's useless if you don't have a proper workflow to run them. With this integration you can run your unit test in a single run or get into tdd mode using an npm script. Also the test need to pass in order to make a `git push`.

Your code is in TypeScript and so should your test files. That way if a test fails it's easier to see if its due to a change in the contract or an actual bug.

#### Why mocha + chai + sinon:
* ✅ It's been proven over and over / Well known in the community.
* ✅ Decoupled test runner from the assertion and or mock library.
* 🚫 By default it runs all the test sequentially (so it may be slower than others)

#### How to use:

Create a test file next to the file you want to test, using the nomenclature `<file-name>.test.ts`.

If you are running a single pass you have to build the source and test and then run them.

```bash
$ npm run build
$ npm t
# or
$ npm run build-and:test
```

While you are developing you can run in `tdd` mode, so whenever you change a file it gets compiled and the test runned.

```bash
$ npm run tdd
```

🌟 If you install a terminal notifier you can receive growl messages with the test execution results. 🌟

```bash
# How to install growl messages on your platform
# Mac OS X (Darwin):
$ sudo gem install terminal-notifier

# Ubuntu (Linux):
$ sudo apt-get install libnotify-bin
```

TODO: add ci

TODO: Add a gif of growl messages

TODO: Investigate how to run from visual code

TODO: See if we can add a way to create test in a `test` directory as well.

#### How to remove:


```bash
$ yarn remove -D mocha @types/mocha chai @types/chai sinon
```

In the `package.json` remove the scripts "test", "watch:test" and "tdd" and if no other script uses it, remove `npm-run-all` as a dependency.


#### More info
TODO: Add link to sinon, chai and

### Docker

If the node app you are trying to build is intended to be a service of some sort (micro or monolithic) you may want to guarantee that it runs in reliable environment. Using Docker we can specify the version of `os`, `node` and others to reduce the difference between dev, prod and ci environments.

If you want to learn more about Docker you can try [this course (in spanish)](https://www.acamica.com/cursos/128/introduccion-a-docker). To remove docker from the project just delete the `Dockerfile`.

To use docker with this starter project, first create your images with the following command

```bash
$ docker build -t myapp:0.0.1 .
```

where `-t myapp:0.0.1` tags the image as `myapp` in the specific version. Then run an instance of your image like this

```bash
$ docker run myapp
```

Notice that the `Dockerfile` is built in order to take advantage of the `Docker layers`, if you modify the code in the src folder it won't run `yarn install`, but if you change the `package.json` or `yarn.lock` it will.

TODO: add reference for english course on docker

### Visual Studio Code configuration

If you are using [Visual Studio Code](https://code.visualstudio.com/) you have some things preconfigured under the `.vscode`:

* You can [run or debug your *tests*](https://code.visualstudio.com/docs/editor/debugging) by selecting the `Run tests` [launch configuration](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations).
* You can [run or debug your *program*](https://code.visualstudio.com/docs/editor/debugging) by selecting the `Launch Program` [launch configuration](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations).
* You can replay the run by pressing F5.
* When editing typescript files you get `fix lint on save`.
* You can build the project by doing `⌘⇧B`.
* Build and tag a docker image using the `docker-build` [task](https://code.visualstudio.com/docs/editor/tasks).
* Build, tag and run a docker image using the `Buid and Launch Docker` [launch configuration](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations).

TODO:
-----
* Add package deps upgrade tool
* Add automatic changelog
* Add automatic semver
* Add CI
* Add doc generation
* Add testing coverage
* Add readme badges
* Maybe: Create branch with FRP using rx and ramda
* Maybe: Create branch with express and knex
* Maybe: Create branch with CLI using commander or similar

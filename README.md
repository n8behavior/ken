# Ken

> A swanky learn'n system, ya' ken?

#### Prerequisites

- AWS [account](https://console.aws.amazon.com/billing/home?#/account) with full
  access to core services, including:
  - IAM
  - S3
  - CloudFormation
  - CloudFront (for production level deploys)
- [`aws`](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
  CLI
  [configured](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)
  with a user or role with access above
- [`npm`](https://www.npmjs.com/get-npm)
  - Recommend [`nvm`](https://github.com/nvm-sh/nvm) with `--lts`
- [`git`](https://git-scm.com/downloads)

While not strictly required, I recommend BASH shell for this tutorial.  Mac and
Linux users are ready out-of-the-box.  Windows users should try
[WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10), it's pretty
good!

## Tooling setup

Globally install [Vue](https://cli.vuejs.org/guide/installation.html) and
[Amplify](https://aws-amplify.github.io/docs/cli/init#install-the-cli) CLI tools

```
npm install -g @vue/cli
npm install -g @vue/cli-init
npm install -g @aws-amplify/cli
amplify configure
```

## Project setup

Use the [PWA template](https://github.com/vuejs-templates/pwa) with `vue` CLI to
generate the initial project skeleton.

```
vue init pwa [project name]
```

Use [`amplify`](https://aws-amplify.github.io/docs/cli/init#amplify-init) to
connect your app with an AWS backend and setup hosting. This is done in the root
for your project.

```
cd [project root]
amplify init
amplify hosting add
```

Use `git` to setup and push our new project into version control.  Remember to
**create your repo** first!
```

git init
git add .
git commit -m "Creation of a master amplify environment"
git remote add origin git@github.com:[project name]
git push -u origin master
```

At this point we have a complete (albeit boring) app ready to be built and
deployed to AWS.  We can do a quick test by running our app locally.

```
npm start
```

That will build/serve our app and launch it in our browser, complete with live
reload.  Or we can push it to AWS for all the world to see.

```
amplify publish
```

## Multi-env setup

Setup a [dev
environment](https://aws-amplify.github.io/docs/cli/multienv?sdk=js) in AWS so
we can have a simple workflow *i.e.* `dev`&rarr;`prod`. Push the `dev`
environment config to our `master` branch.  Then create a `dev` branch so we
have a one-to-one relationship between Git branches and AWS environments.

```
amplify env add
git add .
git commit -m "Creation of a dev amplify environment"
git push
git checkout -b dev
git push -u origin dev
```

## Using multiple enviroments

Get into dev

```
git checkout dev
amplify env checkout dev
```

Do some work, commit/integrate, and test locally

```
npm start
vi src/components/Hello.vue
```

Once it looks good, push & publish to dev env and review testing

```
git add .
git commit -m'Tweak hello msg'
git pull --rebase
git push
amplify publish
```

If good, merge to master and publish to prod env

```
git checkout master
git rebase dev
git push
amplify env checkout master
amplify publish
```

## Build Commands

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For detailed explanation on how things work, checkout the
[guide](http://vuejs-templates.github.io/webpack/) and [docs for
vue-loader](http://vuejs.github.io/vue-loader).



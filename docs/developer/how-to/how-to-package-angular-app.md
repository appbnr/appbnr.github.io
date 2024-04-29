# How to package and release Angular App

> In this how-to, assume you are admin of an organization called as `demo`.
> Read [instructions](how-to-create-an-organization.md) here on how to create an organization for yourself.

## Step 1: create a new app
Using Angular CLI `ng` to create a new project called `hello-world`.

```
ng new hello-world
```

Open project in Visual code and run. If you already add Visual Code into PATH, then:
```
cd hello-world
code .
```

Run following command from Visual Code terminal:
```
npm start
```

You will see site is running.

## Step 2: build and package Appbnr app

Make a new directory under project root called as `appbnr`, then create two files in it:

### Metadata file: package.yml
> Here is the [package.yml specification](../specs/bundle-metadata-spec.md).

```yml
schemaVersion: 1.0.0

code: hello-world
name: Hello World
description: Say hello to the world
developer: demo
visibility: Public
copyright: © 2024 Demo
defaultBasePath: hello-world

release:
  version: 0.0.1
  summary: Initial release

```

### Package script
Create a new file `package.sh` in appbnr folder.

```bash
#!/bin/bash

PROJ_MODULE="hello-world"
PKG_NAME="hello-world@demo"
PKG_VERSION="0.0.1"
REL_PATH="hello-world"

DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
cd $DIR/../

# Angular build
ng build --base-href /$REL_PATH/

# Prepare Appbnr package folder ./tmp/build
rm -rf ./tmp/build
mkdir -p ./tmp/build

cp -r ./dist/$PROJ_MODULE/browser ./tmp/build/app
cp $DIR/package.yml ./tmp/build/.

# Package content in folder
cd ./tmp/build
zip -rq $PKG_NAME-$PKG_VERSION.zip .

```

Make `package.sh` executable, run command in project root folder in Visual Code terminal:

```bash
chmod +x ./appbnr/package.sh
```

## Appbnr upload and install

Following command will upload and release app to appbnr.

```bash
# Login to abnr, you may login with developer access token if first time.
abnr login 

## abnr bundle upload <path to bundle>
abnr bundle upload ./tmp/build/hello-world@demo-0.0.1.zip

## abnr bundle install <org> <app> <version> <path> [overwrite: true | false]
abnr bundle install demo hello-world@demo 0.0.1 hello-world true
```

If everything is good, congrats, you have now built and released your first application in Appbnr platform!

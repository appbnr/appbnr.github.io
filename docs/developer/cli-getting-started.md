# Getting started with Appbnr
  
The Appbnr CLI is a command-line interface tool that you use to interact with Appbnr directly from a command shell.
  
## Prerequisites

* Install [Node.js](https://nodejs.org) which includes [Node Package Manager](https://www.npmjs.com/get-npm).

## Installation

Install the Appbnr CLI globally:

```bash
npm install -g @appbnr/cli
abnr --version
```

## Usage

### Login and Logout
Login:
```bash
abnr login [client_id] [client_secret] [--save]
```

* `client_id` and `client_secret`, check [developer-access-token.md](./developer-access-token.md) for more details
* `--save` add this option if saving `client_id` and `client_secret` into local `.env` file

>`.env` file located in `~/.abnr/cli/.env`, it will store `access_token` if login successfully. Optionally, `client_id` and `client_secret` may be saved as well if `--save` option provided.

Logout
```bash
abnr logout
```
* `access_token` will be removed from local `.env` file.


### Bundle upload and install
Upload
```bash
abnr bundle upload <bundle_file_path>
```
* `bundle_file_path` will point to bundle file locally
> This can upload bundle for same app version if the selected version has not been marked as released.

Install

```bash
abnr bundle install <org> <app> <version> <path> [overwrite]
```
* `org`: organization code
* `app`: application code, for example `short_code@develoepr_code`
* `version`: version of the bundle
* `path`: where the app installed
* `overwrite`: `true` to overwrite already installed app

> `overwrite` can be omited which will report CONFLICT if app already installed.

Release

```bash
abnr bundle release <app> <ver>
```
* `org`: application code, for example `short_code@develoepr_code`
* `ver`: version of the app

> Once version marked as released, it will not be able to upload new bundle file for this version.

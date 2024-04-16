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
```bash
abnr login [client_id] [client_secret]
abnr logout
```

### Bundle upload
```bash
abnr upload [path to bundle file]
```

### Application upload
```bash
abnr install [org] [app] [version] [path] [overwrite]
```

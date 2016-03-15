# npm-link-peer-require

Repo demonstrates [issue](https://github.com/nodejs/node/issues/5726) when trying to require peer dependency from the linked module.

## Environment

* Platform: Windows 10 Pro x64 Build 10586
* Node: 5.8.0
* NPM: 3.7.3

## Steps to reproduce

### Requiring linked peer module from linked module - fails

* run `npm link` in _dep1_ directory
* run `npm link` in _dep2_ directory
* run `npm link dep1` in _app_ directory
* run `npm link dep2` in _app_ directory
* run `node app/index.js`

Process will fail to find _dep2_ module from within _dep1_ module.

### Requiring linked peer module from regular module - works

Following the setup from previous step and doing this...

* run `npm unlink dep1` in _app_ directory
* copy _dep1_ directory into _app/node_modules_ directory
* run `node app/index.js`

The _dep2_ module is now successfully loaded, but...

### Requiring regular peer module from linked module - fails

* run `npm install` in _app_ directory first
* run `node app/index.js`

The `debug` module is required from _dep2_ module which is linked, but it cannot be found.

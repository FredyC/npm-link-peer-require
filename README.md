# npm-link-peer-require

Repo demonstrates issue when trying to require peer dependency from the linked module.

## Environment

Platform: Windows 10 Pro x64 Build 10586
Node: 5.8.0
NPM: 3.7.3

## Steps to reproduce

* run `npm link` in _dep1_ directory
* run `npm link` in _dep2_ directory
* run `npm link dep1` in _app_ directory
* run `npm link dep2` in _app_ directory
* run `node app/index.js`

Process will fail to find _dep2_ module from within _dep1_ module.

## What works...

When requiring linked from regular module, everything works correctly.

* run `npm unlink dep1` in _app_ directory
* copy _dep1_ directory into _app/node_modules_ directory
* run `node app/index.js`

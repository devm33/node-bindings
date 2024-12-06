[@devm33/bindings](https://www.npmjs.com/package/@devm33/bindings)
=============

Fork of [node-bindings](https://github.com/TooTallNate/node-bindings),
re-purposed for use in a bundled environment.

The original node-bindings attempts to load native addons by walking a series of
known paths relative to the executing file's `node_modules` folder. This doesn't
work well for a bundled use case where there is no `node_modules` folder and the
native addons need to be placed alongside the bundled file.

The approach used by this fork is to look for the native addons where the build
process places them. The goal is to support loading modules both in an bundled
case and in a non-bundled case.

The bundled case is determined by looking for a neighboring `compiled`
directory. The non-bundled case is determined by looking for a `dist/compiled`
when walking up the filesystem from the current file.
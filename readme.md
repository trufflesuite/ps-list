# ps-list

> Get running processes

Works on macOS, Linux, and Windows.

## Fork

This is a fork of ps-list (https://github.com/sindresorhus/ps-list), providing a fully JavaScript implementation (leveraging native operating system utilities), and supports only CommonJS module resolution.

The upstream PR [#21 Improve Windows Performance](https://github.com/sindresorhus/ps-list/pull/21) introduces [fast-list](https://github.com/MarkTiedemann/fastlist) as a binary dependency (released in [ps-list@6.0.0](https://github.com/sindresorhus/ps-list/releases/tag/v6.0.0)). This fork reverts to use the native Windows task-list util, which is slower, but doesn't require binaries to be bundled with the package.

## Install

```sh
npm install @trufflesuite/ps-list
```

## Usage

```js
import psList from "@trufflesuite/ps-list";

console.log(await psList());
//=> [{pid: 3213, name: 'node', cmd: 'node test.js', ppid: 1, uid: 501, cpu: 0.1, memory: 1.5}, …]
```

## API

### psList(options?)

Returns a `Promise<object[]>` with the running processes.

On macOS and Linux, the `name` property is truncated to 15 characters by the system. The `cmd` property can be used to extract the full name.

The `cmd`, `cpu`, `memory`, and `uid` properties are not supported on Windows.

#### options

Type: `object`

##### all

Type: `boolean`\
Default: `true`

Include other users' processes as well as your own.

On Windows this has no effect and will always be the users' own processes.

## Related

- [tasklist](https://github.com/sindresorhus/ps-list) - The JavaScript wrapper around the native Windows `tasklist` util.

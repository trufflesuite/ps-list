# ps-list

> Get running processes

Works on macOS, Linux, and Windows.

## Fork

Note: this is a fork of ps-list (https://github.com/sindresorhus/ps-list), in order to provide a fully JavaScript implementation. This reverts the Windows implementation to use task-list (https://github.com/sindresorhus/ps-list/pull/21, upgraded in ps-list@6.0.0 to use fast-list https://github.com/MarkTiedemann/fastlist).

## Install

```sh
npm install ps-list
```

## Usage

```js
import psList from 'ps-list';

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

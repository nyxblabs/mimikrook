[![cover][cover-src]][cover-href]
[![npm version][npm-version-src]][npm-version-href] 
[![npm downloads][npm-downloads-src]][npm-downloads-href] 
[![bundle][bundle-src]][bundle-href] 
[![License][license-src]][license-href]

# 🪄 Mimikrook

> 🎣🔗 Mimikrook: Awaitable hooks for seamless code enhancement! 💪💡 Boost your development with the power of hooks. 🚀

## 📦 Install:

Using yarn:

```bash
# nyxi
nyxi mimikrook

# pnpm
pnpm add mimikrook

# npm
npm i mimikrook

# yarn
yarn add mimikrook
```

## 📘 Usage

**Method 🅰️: Create a mimikrook instance:**

```ts
import { createHooks } from 'mimikrook'

// Create a mimikrook instance
const hooks = createHooks()

// Hook on 'hello'
hooks.hook('hello', () => { console.log('Hello World') })

// Call 'hello' hook
hooks.callHook('hello')
```

**Method 🅱️: Extend your base class from Mimikrook:**

```ts
import { Mimikrook } from 'mimikrook'

export default class FooLib extends Mimikrook {
   constructor() {
      // Call to parent to initialize
      super()
      // Initialize Mimikrook with custom logger
      // super(consola)
   }

   async someFunction() {
      // Call and wait for `hook1` hooks (if any) sequential
      await this.callHook('hook1')
   }
}
```

**🔌 Inside plugins, register for any hook:**

```ts
const lib = new FooLib()

// Register a handler for `hook2`
lib.hook('hook2', async () => { /* ... */ })

// Register multiply handlers at once
lib.addHooks({
   hook1: async () => { /* ... */ },
   hook2: []
})
```

**🗑️ Unregistering hooks:**

```ts
const lib = new FooLib()

async function hook0() { /* ... */ }
async function hook1() { /* ... */ }
async function hook2() { /* ... */ }

// The hook() method returns an "unregister" function
const unregisterHook0 = lib.hook('hook0', hook0)
const unregisterHooks1and2 = lib.addHooks({ hook1, hook2 })

/* ... */

unregisterHook0()
unregisterHooks1and2()

// or

lib.removeHooks({ hook0, hook1 })
lib.removeHook('hook2', hook2)
```

**🔂 Triggering a hook handler once:**

```js
const lib = new FooLib()

const unregister = lib.hook('hook0', async () => {
   // Unregister as soon as the hook is executed
   unregister()

   /* ... */
})
```


## 🏫 Mimikrook class

### 🏗️ `constructor()`

### 🪝 `hook (name, fn)`

Register a handler for a specific hook. `fn` must be a function.

Returns an `unregister` function that, when called, will remove the registered handler.

### 🕒 `hookOnce (name, fn)`

Similar to `hook` but unregisters hook once called.

Returns an `unregister` function that, when called, will remove the registered handler before first call.

### 📐 `addHooks(configHooks)`

Flatten and register hooks object.

 💡Example:

```ts
mimikrook.addHooks({
   test: {
      before: () => {},
      after: () => {}
   }
})
```

This registers `test:before` and `test:after` hooks at bulk.

Returns an `unregister` function that, when called, will remove all the registered handlers.

### 📞 `async callHook (name, ...args)`

Used by class itself to **sequentially** call handlers of a specific hook.

### 📞 `callHookWith (name, callerFn)`

If you need custom control over how hooks are called, you can provide a custom function that will receive an array of handlers of a specific hook.

`callerFn` if a callback function that accepts two arguments, `hooks` and `args`:
- `hooks`: Array of user hooks to be called
- `args`: Array of arguments that should be passed each time calling a hook

### ⚠️ `deprecateHook (old, name)`

Deprecate hook called `old` in favor of `name` hook.

### ⚠️ `deprecateHooks (deprecatedHooks)`

Deprecate all hooks from an object (keys are old and values or newer ones).

### 🗑️ `removeHook (name, fn)`

Remove a particular hook handler, if the `fn` handler is present.

### 🗑️ `removeHooks (configHooks)`

Remove multiple hook handlers.

💡 Example:

```ts
async function handler() { /* ... */ }

mimikrook.hook('test:before', handler)
mimikrook.addHooks({ test: { after: handler } })

// ...

mimikrook.removeHooks({
   test: {
      before: handler,
      after: handler
   }
})
```

### 🗑️ `removeAllHooks`

Remove all hook handlers.

### ⏮️ `beforeEach (syncCallback)`

Registers a (sync) callback to be called before each hook is being called.

```ts
mimikrook.beforeEach((event) => { console.log(`${event.name} hook is being called with ${event.args}`)}`)
mimikrook.hook('test', () => { console.log('running test hook') })

// test hook is being called with []
// running test hook
await mimikrook.callHook('test')
```

### ⏭️ `afterEach (syncCallback)`

Registers a (sync) callback to be called after each hook is being called.

```ts
mimikrook.afterEach((event) => { console.log(`${event.name} hook called with ${event.args}`)}`)
mimikrook.hook('test', () => { console.log('running test hook') })

// running test hook
// test hook called with []
await mimikrook.callHook('test')
```

### 🔍 `createDebugger`

Automatically logs each hook that is called and how long it takes to run.

```ts
const debug = mimikrook.createDebugger(hooks, { tag: 'something' })

hooks.callHook('some-hook', 'some-arg')
// [something] some-hook: 0.21ms

debug.close()
```

🐙 Clone this repository
🔧 Enable [Corepack](https://github.com/nodejs/corepack) using `corepack enable`
📦 Install dependencies using [nyxi](https://github.com/nyxblabs/nyxi) 🧙 Always right package manager

## 📜 License

[MIT](./LICENSE) - Made with 💞

<!-- Badges -->

[npm-version-src]: https://img.shields.io/npm/v/mimikrook?style=flat&colorA=18181B&colorB=14F195
[npm-version-href]: https://npmjs.com/package/mimikrook
[npm-downloads-src]: https://img.shields.io/npm/dm/mimikrook?style=flat&colorA=18181B&colorB=14F195
[npm-downloads-href]: https://npmjs.com/package/mimikrook
[bundle-src]: https://img.shields.io/bundlephobia/minzip/mimikrook?style=flat&colorA=18181B&colorB=14F195
[bundle-href]: https://bundlephobia.com/result?p=mimikrook
[license-src]: https://img.shields.io/github/license/nyxblabs/mimikrook.svg?style=flat&colorA=18181B&colorB=14F195
[license-href]: https://github.com/nyxblabs/mimikrook/blob/main/LICENSE

<!-- Cover -->
[cover-src]: https://raw.githubusercontent.com/nyxblabs/mimikrook/main/.github/assets/mimikrook.png
[cover-href]: https://💻nyxb.ws

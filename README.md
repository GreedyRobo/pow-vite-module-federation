## Q&A

### Do modules lazily load on the client side or are they prebuilt?
Modules are not statically prebuilt and loading dynamically while the app is running on the client side.

### Can you use Vite `dev` mode?
You can use `dev` mode only while developing module individually, once you are running `host` app all modules must be prebuilt and served using `preview` command. 

Note from package docs:

> Only the Host side supports dev mode, the Remote side requires the RemoteEntry.js package to be generated using vite build. This is because Vite Dev mode is Bundleless and you can use vite build --watch to achieve a hot update effect.

However, I'm still struggling to run host app in `dev` mode, while everything works with `build` and `preview` commands.


### Do we need to module build order?
Yes, first we need to build remote components and then run host app build.

### What can be improved in this repo?
1) Find a better way how to share eslint config as tsconfig.
2) Declare remote modules to resolve Typescript "Cannot find module" error.
3) Provide more complex components with dependencies to some packages instead of plain text.

### Is it worth it?
In this example we are using `@originjs/vite-plugin-federation` package which is becoming outdated and author itself suggest
to use `@module-federation/vite` package which is still in early stage of development
(https://github.com/originjs/vite-plugin-federation/issues/597). Alternatively,
it is possible to use https://rspack.dev/guide/features/module-federation for module federation.
# nextjs-standalone-esm-bug

To start

```
npm install
```

When having a combination of:

- `"type": "module"` in `package.json`
- `output: 'standalone'` in `next.config.mjs`
- A custom directory to build from when running `npm run build custom-dir`

Then running:

```bash
npm run build custom-dir
```

The output in `custom-dir/.next/standalone/custom-dir/server.js` is not ESM compatible.

This means we cannot do:

```
node custom-dir/.next/standalone/custom-dir/server.js
```

without getting a reference error `ReferenceError: require is not defined in ES module scope, you can use import instead`.

Expected outcome is for standalone output to be ESM code.

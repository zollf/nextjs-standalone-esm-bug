# nextjs-standalone-esm-bug

When having a combination of:

- `"module": "NodeNext"` in `tsconfig.json`
- `"moduleResolution": "NodeNext"` in `tsconfig.json`
- `"type": "module"` in `package.json`
- `output: 'standalone'` in `next.config.mjs`
- A custom directory to build from when running `npm run build custom-dir`

Then running:

```bash
npm run build custom-dir
```

The output in `custom-dir/.next/standalone/custom-dir/server.js` is not ESM compatible.

Expected outcome is for standalone output to be ESM code.

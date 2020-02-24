# tsc-compile-Map

Map は target どこまででトランスパイルできるか

```
yarn tsc main.ts --outFile bundle.js
```

何も指定しないなら怒られる（ES5 向けに吐き出される）

```
❯ yarn tsc main.ts --outFile bundle.js
yarn run v1.19.1
$ toybox/tsc-compile-Map/node_modules/.bin/tsc main.ts --outFile bundle.js
main.ts:1:18 - error TS2583: Cannot find name 'Map'. Do you need to change your target library? Try changing the `l
ib` compiler option to es2015 or later.

1 const hoge = new Map();
                   ~~~


Found 1 error.

error Command failed with exit code 2.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```

target を指定すると成功する

```
❯ yarn tsc main.ts --outFile bundle.js --target  ES6
yarn run v1.19.1
$ /tsc-compile-Map/node_modules/.bin/tsc main.ts --outFile bundle.js --target ES6
✨  Done in 2.43s.
```

ES5 向けに Map を使うにはどうすればいいか -> polyfill を突っ込む

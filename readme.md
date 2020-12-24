
this example is a demo of lib: https://github.com/tleunen/babel-plugin-module-resolver

## Update:
babel-plugin-module-resolver new version seems to have worked when import from App.js (root tree)
And react native version > 60 they replaced `.babelrc` to `babel.config.js`
so we have to edit `babel.config.js` instead `.babelrc`
like this:
```
module.exports = {
  presets: ['module:metro-react-native-babel-preset'],
  plugins: [
    [
      "module-resolver",
      {
        "root": [
          "./src"
        ],
        extensions: [
          '.ios.ts',
          '.android.ts',
          '.ts',
          '.ios.tsx',
          '.android.tsx',
          '.tsx',
          '.jsx',
          '.js',
          '.json',
        ],
        "alias": {
          "components": "./src/components",
          "reducers": "./src/reducers",
          "app": "./src",
        }
      }
    ]
  ]
};
```
reference of update: https://medium.com/@aleksefo/how-to-setup-module-resolution-and-path-aliases-with-react-native-and-typescript-f4924669780a

note:

~~babel-plugin-module-resolver doesn't work when import from App.js (root tree)~~ ( now it worked )

**See more [Issue](https://github.com/hungdev/react-native-alias-example/issues/1#issuecomment-457250312)**


docs: https://github.com/tleunen/babel-plugin-module-resolver/blob/master/DOCS.md

step1:
```
npm install --save-dev babel-plugin-module-resolver
```

step2: config .babelrc like this:

```
{
  "presets": [
    "module:metro-react-native-babel-preset"
  ],
  "plugins": [
    [
      "module-resolver",
      {
        "cwd": "babelrc",
        "root": [
          "./src"
        ],
        "extensions": [
          ".js",
          ".ios.js",
          ".android.js"
        ],
        "alias": {
          "components": "./src/components",
          "app": "./src",
        }
      }
    ]
  ]
}
```

step3: use, import:

like this
```
import Demo from 'app/Demo'
```

or like this

```
import App from 'app'
```


for react, read here https://www.robinwieruch.de/babel-module-resolver

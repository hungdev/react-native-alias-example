
this example is a demo of lib: https://github.com/tleunen/babel-plugin-module-resolver

note:

babel-plugin-module-resolver doesn't work when import from App.js (root tree)

** See more [Issue](https://github.com/hungdev/react-native-alias-example/issues/1#issuecomment-457250312)


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



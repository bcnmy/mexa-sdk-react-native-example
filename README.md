

```sh
yarn install
cd ios
pod install
cd ..

yarn add @biconomy/mexa
# import and made onPress changes
npx react-native run-ios

# for ios https://stackoverflow.com/a/74244642/11097431
open node_modules/react-native/scripts
# make changes in launchPackager.command

# now for polyfill issue
# https://stackoverflow.com/a/52698050/11097431
# https://github.com/rainbow-me/rainbow/blob/develop/package.json
yarn add react-native-crypto
# install peer deps 
yarn add react-native-randombytes
react-native link react-native-randombytes
# install latest rn-nodeify 
yarn add -D tradle/rn-nodeify
# install node core shims and recursively hack package.json files 
# in ./node_modules to add/update the "browser"/"react-native" field with relevant mappings 
./node_modules/.bin/rn-nodeify --hack --install
# rn-nodeify will create a shim.js in the project root directory index.ios.js or index.android.js
# make sure you use `import` and not require!
# import './shim.js'

```
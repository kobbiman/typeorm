# Supported platforms

* [NodeJS](#nodejs)
* [Browser](#browser)
* [Cordova / PhoneGap / Ionic apps](#cordova-phonegap-ionic-apps)
* [NativeScript](#nativescript)

## NodeJS

TypeORM was tested on Node.js version 4 and above. 

## Browser

There is an experimental version of TypeORM that runs in the browser using WebSQL.
There are two ways how it can be used in browser:

* **Webpack / ES2015 Module**
    
    In the `browser` folder the package also includes a version compiled as a ES2015 module. If you want to use a different loader this is the point to start. The package is setup in a way that loaders like webpack will automatically use the `browser` folder.

* **SystemJS**
    
    If you want to use SystemJS as a module loader than three precompiled files are included for you to use.
    
    ```
    - typeorm-browser.js
    - typeorm-browser.min.js (Minified version)
    - typeorm-browser.js.map (Sourcemap)
    ```

Since these files are generated by the TypeScript compiler they are affected by the [issue, that SystemJS 0.20 does not support them](https://github.com/systemjs/systemjs/issues/1587). When using SystemJS@0.19.47 everything works.
For an example see [typeorm/browser-example](https://github.com/typeorm/browser-example).

**Example of configuration**

```typescript
createConnection({
    type: "websql",
    database: "test",
    version: 1,
    description: "test database",
    size: 2 * 1024 * 1024,
    entities: [
        Photo
    ],
    synchronize: true
});
```

**Don't forget to include reflect-metadata**
    
Don't forget to include reflect-metadata in your html:

```html
<script src="./node_modules/reflect-metadata/Reflect.js"></script>
```

## Cordova / PhoneGap / Ionic apps

TypeORM is able to run on Cordova, PhoneGap, Ionic apps using the
[cordova-sqlite-storage](https://github.com/litehelpers/Cordova-sqlite-storage) plugin
You have the option to choose between module loaders just like in browser package. 
For an example how to use TypeORM in Cordova see [typeorm/cordova-example](https://github.com/typeorm/cordova-example) and for Ionic see [typeorm/ionic-example](https://github.com/typeorm/ionic-example).

## NativeScript

In the next releases we are planning to support NativeScript platform as well.

Please feel free to join a community and help us with new features and supporting a new platforms!
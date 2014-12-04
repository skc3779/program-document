# NodeJs 사용법


### npm install

### npm delete

```cmd
$> npm uninstall [@<scope>/]<package> [--save|--save-dev|--save-optional]
```
In global mode (ie, with -g or --global appended to the command), it uninstalls the current package context as a global package.

### npm find

```cmd
$> npm list | grpe -n "이름"
```

```cmd
This prints the version of npm itself:
npm -v <package-name>

This prints a cryptic error:
npm version <package-name>

This prints the package version on the registry (i.e. the latest version available):
npm view <package-name> version
```

npm list for local packages or npm list -g for globally installed package

```cmd
├─┬ cli-color@0.1.6 
│ └── es5-ext@0.7.1 
├── coffee-script@1.3.3 
├── less@1.3.0 
├─┬ sentry@0.1.2 
│ ├── file@0.2.1 
│ └── underscore@1.3.3 
└── uglify-js@1.2.6 
```


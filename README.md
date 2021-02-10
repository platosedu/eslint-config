# Eslint Config
Eslint configuration with Typescript and Prettier support by default. This settings is used across all JavaScript/Typescript projects at [Platos Educational](http://www.platosedu.com.br/).

## Using

### 1. Install the library and its dependencies

npm:
```shell
npm install --save-dev @platosedu/eslint-config prettier
```

yarn: 
```shell
yarn add dev @platosedu/eslint-config prettier
```

### 2. Set up the prettier configuration
#### 2.1. Add file `.prettierrc.json`
```json
{
  "trailingComma": "none",
  "semi": false,
  "singleQuote": true,
  "endOfLine": "auto"
}
```

#### 2.2. If you use VSCode, add the file `.vscode/settings.json`
This settings is needed automatize code formatting when a file is saved
```json
{
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.fixAll.tslint": true,
    "source.fixAll.stylelint": true
  }
}
```

### 3. Setup config by enviroment

#### 3.1. NodeJS
##### Add file `.eslintrc.json`
```json
{
  "extends": [
    "@platosedu/eslint-config"
  ],
  "env": {
    "node": true
  }
}
```

#### 3.2. Vanilla JS
##### Add file `.eslintrc.json`
```json
{
  "extends": [
    "@platosedu/eslint-config"
  ],
  "env": {
    "browser": true
  }
}
```

#### 3.3. React JS with create-react-app + import resolver
##### Install babel-plugin-module-resolver
npm:
```shell
npm install --save-dev babel-plugin-module-resolver
```

yarn:
```shell
yarn add dev babel-plugin-module-resolver
```

##### Add file `.eslintrc.json`
```json
{
  "extends": ["@platosedu/eslint-config/react"],
  "env": {
    "browser": true
  },
  "settings": {
    "import/resolver": {
      "babel-module": {
        "root": ["./src/"]
      }
    }
  }
}
```

### 4. Typescript support
This eslint settings was setted up to support typescript by default.

#### 4.1.
In order to support typescript on your project, you will need your own typescript config with your preferences. See below an example.

`tsconfig.json`
```json
{
  "compilerOptions": {
    "allowJs": true,
    "alwaysStrict": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "lib": ["dom", "es2017"],
    "module": "esnext",
    "moduleResolution": "node",
    "noEmit": true,
    "noFallthroughCasesInSwitch": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "resolveJsonModule": true,
    "skipLibCheck": true,
    "strict": true,
    "target": "esnext"
  },
  "exclude": ["node_modules"],
  "include": ["**/*.ts", "**/*.tsx"]
}
```

#### 4.2. Typescript module resolver
To support a customized base path for imports you need to add the `baseUrl` option on your `tsconfig.json` file. See below:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "alwaysStrict": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "lib": ["dom", "es2017"],
    "module": "esnext",
    "moduleResolution": "node",
    "noEmit": true,
    "noFallthroughCasesInSwitch": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "resolveJsonModule": true,
    "skipLibCheck": true,
    "strict": true,
    "target": "esnext"
  },
  "exclude": ["node_modules"],
  "include": ["**/*.ts", "**/*.tsx"]
}
```
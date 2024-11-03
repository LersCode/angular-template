# Install Jest

## Installing Jest

### 1️⃣ Install
```bash
npm install jest @types/jest @jest/globals jest-preset-angular --save-dev
```

Modified files: `package.json` and `package-lock.json` 

### 2️⃣ Now remove all the libraries related to Karma and Jasmine.

🛑 NOT `@types/jasmine` OR `jasmine-core`
```bash
npm uninstall karma karma-chrome-launcher karma-coverage karma-jasmine karma-jasmine-html-reporter
```

> Note: Make sure to just uninstall the libraries you actually have installed in your application.

### 3️⃣ Remove any files related to Karma, like karma.conf.js and src/test.ts files.
    
```bash
rm ./karma.conf.js ./src/test.ts
```

## Configure Jest

### 4️⃣ Configure the TS Config Spec file to include the types for Jest. 
Here is an example configuration:

```json
// tsconfig.spec.json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/spec",
    "module": "CommonJs",
    "types": ["jest"]
  },
  "include": ["src/**/*.spec.ts", "src/**/*.d.ts"]
}
```

### 5️⃣ Create a jest-setup-file

Create file `setup-jest.ts` and add the following line:

```typescript
import "jest-preset-angular/setup-jest";
```

### 5️⃣ Create a jest-config-file

Create file `jest.config.js` and add the follwing:

```javascript
module.exports = {
    preset: 'jest-preset-angular',
    setupFilesAfterEnv: ['<rootDir>/setup-jest.ts'],
    globalSetup: 'jest-preset-angular/global-setup',
};
```

### 6️⃣ Remove test runner from `angular.json`

Remove the `"test":{}`-part from your angular.json

## Run Jest

### Migration of existing tests

If you already have existing tests, you need to migrate them to Jest. The following command can help:

```bash
npx jest-codemods
```

### Run Jest tests

```bash
jest
```
```bash
jest --coverage
```

### You can add these commands to your package.json 
```json
// package.json
"scripts": [
"test": "jest",
"test:coverage": "jest --coverage"
]
```


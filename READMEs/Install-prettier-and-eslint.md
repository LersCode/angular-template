# Install ESLint & Prettier into an Angular App

## Install ESLint

```bash
ng add @angular-eslint/schematics
```

- Added files: `.eslintrc.json`
- Modified files: `package.json`, `package-lock.json` and `angualar.json`

#### All your linting rules can be added in the `.eslintrc.json`.

## Install Prettier

```bash
npm install prettier --save-dev
```

Create a file in the `root` of your project: `.prettierrc.json`.
<br>[Have a look at the available Rules!](https://prettier.io/docs/en/options.html)


- Added files: `.prettierrc.json`
- Modified files: `package.json` and `package-lock.json`

#### All your linting rules can be added in the `.prettierrc.json`.

## Make Prettier work with ESLint

```bash
npm install prettier-eslint eslint-config-prettier eslint-plugin-prettier --save-dev
```

After installation we add `"plugin:prettier/recommended"` into our `.eslintrc.json`:

```json
"overrides": [
        {
            "files": ["*.ts"],
            "extends": [
                "eslint:recommended",
                "plugin:@typescript-eslint/recommended",
                "plugin:@angular-eslint/recommended",
                "plugin:@angular-eslint/template/process-inline-templates",
                "plugin:prettier/recommended" // <--- Here
            ],
...
```

If you now run `ng lint` you might get multiple errors. If you want them to be fixed automatically, run `ng lint --fix`. Some might still need manual modification.

## Finished 🏁
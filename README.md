# frontend-survival-week01

프론트엔드 생존코스 1주차 과제

## frontend Boilerplate

### 프로젝트 생성

- .gitignore
  - [참고링크](https://github.com/github/gitignore)

```bash
npm init -y
touch .gitignore
```

### eslint 설치

```bash
npm i -D eslint # eslint 설치
touch .eslintrc.js
touch .eslintignore # eslint 예외 파일 설정
```

- .eslintrc.js

```json
module.exports = {
  env: {
    browser: true,
    es2021: true,
    jest: true,
  },
  extends: [
    "xo",
    "plugin:prettier/recommended",
    "plugin:react/recommended",
    "plugin:react/jsx-runtime",
  ],
  overrides: [
    {
      env: {
        node: true,
      },
      files: [".eslintrc.{js,cjs}"],
      parserOptions: {
        sourceType: "script",
      },
    },
    {
      extends: ["xo-typescript"],
      files: ["*.ts", "*.tsx"],
    },
  ],
  parserOptions: {
    ecmaVersion: "latest",
    sourceType: "module",
  },
  plugins: ["react"],
  rules: {},
};
```

### react 설치

```bash
npm i react react-dom
npm i -D @types/react @types/react-dom
```

### jest 설치

```bash
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom@5.16.4
touch jest.config.js
```

- jest.config.js

```json
module.exports = {
  testEnvironment: "jsdom",
  setupFilesAfterEnv: ["@testing-library/jest-dom/extend-expect"],
  transform: {
    "^.+\\.(t|j)sx?$": [
      "@swc/jest",
      {
        jsc: {
          parser: {
            syntax: "typescript",
            jsx: true,
            decorators: true,
          },
          transform: {
            react: {
              runtime: "automatic",
            },
          },
        },
      },
    ],
  },
  testPathIgnorePatterns: ["<rootDir>/node_modules/", "<rootDir>/dist/"],
};

```

### parcel 설치

```bash
npm i -D parcel
touch .parcelrc
```

- .parcelrc

```json
{
  "extends": ["@parcel/config-default"],
  "reporters": ["...", "parcel-reporter-static-files-copy"]
}
```

### 프로젝트 실행

```bash
npm i
npm run start
```

### 프로젝트 배포

```bash
npm i
npm run build
npx servor ./dist
```

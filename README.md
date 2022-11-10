# appDir compiled React issue

## Problem

`nextConfig.experimental.appDir=true` uses compiled `react` version which is `18.3.0-next-28a574ea8-20221027`.
The normal React version in this `create-next-app` is `18.2.0`
This causes types errors when using libraries like `react-hook-form` because of version mismatch:

```
error - TypeError: Cannot read properties of null (reading 'useRef')
    at Object.useRef (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/react/cjs/react.development.js:1630:21)
    at useForm (file:///Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/react-hook-form/dist/index.esm.mjs:2267:32)
    at Home (webpack-internal:///./pages/index.tsx:23:83)
    at renderWithHooks (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/next/dist/compiled/react-dom/cjs/react-dom-server.browser.development.js:7629:16)
    at renderIndeterminateComponent (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/next/dist/compiled/react-dom/cjs/react-dom-server.browser.development.js:7702:15)
    at renderElement (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/next/dist/compiled/react-dom/cjs/react-dom-server.browser.development.js:7927:7)
    at renderNodeDestructiveImpl (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/next/dist/compiled/react-dom/cjs/react-dom-server.browser.development.js:8094:11)
    at renderNodeDestructive (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/next/dist/compiled/react-dom/cjs/react-dom-server.browser.development.js:8066:14)
    at renderIndeterminateComponent (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/next/dist/compiled/react-dom/cjs/react-dom-server.browser.development.js:7756:7)
    at renderElement (/Users/eddeee888/Projects/eddeee888/next-compiled-react/next-compiled-react/node_modules/next/dist/compiled/react-dom/cjs/react-dom-server.browser.development.js:7927:7) {
  page: '/'
```

## Reproducing the issue

### From scratch

1. Run `yarn create-next-app` and go through the prompts
1. Run `yarn add react-hook-form`
1. Set `(next.config.js).nextConfig.experimental.appDir=true`
1. Import and call `useForm` in `pages/index.ts`
1. Run `yarn dev`
1. Error will show up in terminal

### Or using what's in this repo

1. Run `yarn install` to install packages
1. Run `yarn dev`
1. Error shows up in the terminal

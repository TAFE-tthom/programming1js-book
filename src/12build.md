# Vite and React

## Build Systems - Vite

Within web-development sphere in the 2020s, a build system has become common as part of developing web applications and mobile applications.

In this subject, we will be using `vite` build system which will be used to generate a react-javascript template that will be the basis of our projects. 

### Why `vite` over just `npm`

Build systems as part of web-development have evolved and this has evolved to address lack of standards within this ecosystem, especially with technologies and tools evolving rapidly.

Given javascript is not supported within the browser, we are needing to transform it to javascript.

### Starting a project with `vite` and `react`

To get started, you can start by building a scaffold of your project using

```
npm create vite@latest  
```

You can then select `React` and `Javascript`.

Once generated, you can see the contents of the template, so lets breakdown each part.

```
public  src  lint.config.js  package.json  README.md
tsconfig.app.json  tsconfig.node.json  index.html
tsconfig.json      vite.config.ts 
```

* `public` - Folder for default files like `index.html`
* `package.json` - scripts and dependencies
* `eslint.config.js` - Default linter configuration
* `vite.config.js` - Configuration file for vite build system
* `src` - Where your javascript files go

With `vite`, the build system also enables running a `development` mode of the webserver that will allow for reloading of the files if changes are detected.

You are able to run the development server using `npm run dev`. This will use the `dev` script within `package.json`.

Within `package.json`, we can observe the following:

```
"scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
}
```

## Single-Page Applications and React

The single page application came from more advanced usage of `AJAX` and retrieving data through javascript and updating the DOM elements.

Web-Frameworks evolved to facilitate more control over the DOM and componentise parts of the DOM rather than having to build up things. While logically there could be multiple pages, from the browser's perspective it is a single page and the DOM is manipulated.

### React

React's perspective on components and modularisation is to treat classes and functions are components which render HTML (or in the case of React-Native, NativeUI components).

Within `main.jsx`, you will observe:

```
<StrictMode>
  <App />
</StrictMode>    
```

The above `App` being a component which is the result of `App()` when rendered. We will explore react components in the next section.

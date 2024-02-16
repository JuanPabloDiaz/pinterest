# jsDoc

## jsDoc for javascript documentation

1. Install `jsdoc` as a dev dependency:

   ```bash
   npm i -D jsdoc
   ```

2. Create a `jsdoc.json` file in the root of your project

   ```json
   {
     "source": {
       "include": ["src"],
       "includePattern": ".js$",
       "excludePattern": "(node_modules/|docs)"
     },
     "plugins": ["plugins/markdown"],
     "templates": {
       "cleverLinks": true,
       "monospaceLinks": true
     },
     "opts": {
       "recurse": true,
       "destination": "*/docs/"
     }
   }
   ```

Explanation:

    > The `source` object is where you specify the files you want to document. In this case, we are including all files in the `src` directory that end with `.js`. We are also excluding files that start with an underscore (`_`), are in the `node_modules` directory, or are in the `docs` directory.
    > jsdoc will be using the `markdown` plugin to parse the `jsDoc-tutorial.md` file and include it in the generated documentation which will be placed in the `docs` directory.

3. Add a script to your `package.json` file to run jsdoc

   ```json
   {
     "scripts": {
       "docs": "jsdoc -c jsdoc.json"
     }
   }
   ```

4. Ensure that the project has a `.js` file in the `src` directory but also that the .js file has jsDoc comments structure like this:

The simplest documentation is just a description

    ```javascript
    /** This is a description of the foo function. */
    function foo() {}
    ```

5. Run the script

   ```bash
   npm run docs
   ```

6. Open the `docs/index.html` file in your browser to see the generated documentation

---

## jsDoc for React Documentation

To configure JSDoc to include JSX files for documentation generation, you need to use a plugin like jsdoc-babel to add JSX support. Here's how you can do it:

1. Install jsdoc and jsdoc-babel as dev dependencies

```bash
npm i -D jsdoc jsdoc-babel
```

2. Create a jsdoc.json configuration file (or modify your existing one) to include the plugin and specify the files to include:

```json
{
  "plugins": ["node_modules/jsdoc-babel"],
  "source": {
    "include": ["src/**/*.{js,jsx}"],
    "includePattern": ".+\\.jsx?$",
    "excludePattern": "(^|\\/|\\\\)_|node_modules/"
  }
}
```

Explanation:

> This configuration will include all .js and .jsx files in the src directory and its subdirectories for documentation generation, and exclude any files in the node*modules directory.
> The `plugins` array includes the jsdoc-babel plugin to add JSX support.
> The `source` object specifies the files to include for documentation generation. In this case, we are including all files in the `src` directory with the extensions `.js` or `.jsx`. We are also excluding files that start with an underscore (`*`) or are in the `node_modules` directory.

3. Add a script to your `package.json` file to run jsdoc

```json
{
  "scripts": {
    "docs": "jsdoc -c jsdoc.json"
  }
}
```

4. Run the script

```bash
npm run docs
```

5. Open the `docs/index.html` file in your browser to see the generated documentation

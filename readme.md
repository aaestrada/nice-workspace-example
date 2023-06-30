# nice-workspace-example
## Configure the basic project:

#### Create an empty directory using the npm initializer:

```
npm init -y
```

now Create the packages

```
npm init -y --scope @nice-workspace-example -w packages/back
npm init -y --scope @nice-workspace-example -w packages/front
npm init -y --scope @nice-workspace-example -w packages/controllers
```

you will see the files extructure as following:

``` markdown
- [**packages**](packages)
    - [**controllers**](packages/controllers)
    - [**back**](packages/back)
    - [**front**](packages/front)
- [nice-workspace-example](readme.md)
```

Share the dependencies needed between the packages

```
npm install @nice-workspace-example/back -w @nice-workspace-example/front
npm install @nice-workspace-example/back -w @nice-workspace-example/controllers
```

### Analize the workspace workflows between the packages:

lets add some simple code to the share package to test it:

update the `packages/back/index.js` as following: 

``` js
console.log("Hello from back!");
```

update the `packages/front/index.js` as well:

``` js
require("@nice-workspace-example/back");
console.log("Hello from front!");
```

finally add this code snipped to the `packages/controllers/index.js` file:

``` js
require("@nice-workspace-example/back");
console.log("Hello from controllers!");
```

and now run your file with node:

``` bin
node packages/controllers/index.js
```

you will see the following output in your console:

```
Hello from back!
Hello from controllers!
```
# Nodemon

## What is this?
Nodemon is a tool that helps develop Node.js based applications by automatically restarting the node application when file changes in the directory are detected.

[official docs](https://www.npmjs.com/package/nodemon)


## How to use?
Create nodemon config in root folder.


## Example
Example for [[typescript]] project with yarn

__`nodemon.json`__
```json
{
	"ignore": ["**/*.spec.ts", "node_modules", "dist", ".git"],
	"watch": ["src"],
	"exec": "yarn start",
	"ext": "ts"
}
```
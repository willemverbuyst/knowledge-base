# Prettier

## What is this?
Code formatter

[Official docs](https://prettier.io/)


## How to use?
Create a prettier config at the root of your project.
Also add a prettierignore.


## Example
__`.prettierrc`__
```json
{
	"semi": false,
	"printWidth": 80,
	"singleQuote": true,
	"tabWidth": 2,
	"bracketSpacing": true,
	"trailingComma": "es5"
}
```

__`.prettierignore`__
```
node_modules
dist
build
```
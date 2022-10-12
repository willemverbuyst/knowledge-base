# Dependabot

## What is this?
Dependabot monitors the repository and creates a PR when dependencies are outdated and can be updated.


## How to use?
In a __`.github`__ folder (at root level) add a config file.


## Examples

__`dependabot.yml`__
```yml
version: 2
updates:
  - package-ecosystem: 'npm'
    directory: '/'
	schedule:
	  interval: 'daily'
	ignore:
	  - dependency-name: 'typescript'
	    versions: ['4.x']
	  - dependency-name: 'webpack'
```

__`dependabot.yml`__
```yml
version: 2
updates:
  - directory: .
    package-ecosystem: 'npm'
	schedule:
	  interval: 'monthly'
	  time: '04:00'
	ignore:
	  - dependency-name: '*'
		update-types: ['version-update:semver-major']
```
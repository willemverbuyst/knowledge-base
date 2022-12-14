# github action

## Build and lint go project

**`./github/workflows/build-lint.yml`**
```yml
name: Server - build & lint

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Setup Go
        uses: actions/setup-go@v2
        with:
          go-version: '1.18.3'
      - name: Install dependencies
        run: go version
      - name: Run build
        run: go build .
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/setup-go@v3
        with:
          go-version: '1.18.3'
      - uses: actions/checkout@v3
      - name: golangci-lint
        uses: golangci/golangci-lint-action@v3
        with:
          version: v1.49
```

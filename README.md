# learn-cicd-starter (Notely)
This repo started from BootDev starter and will track progression
Code implementation checked using BootDev CLI
## 🔹 1. Local Development 
- Make sure you're on Go version 1.22+.
- Create a `.env` file in the root of the project with the following contents:
```bash
PORT="8080"
```

- Run the server:
*This starts the server in non-database mode.* It will serve a simple webpage at `http://localhost:8080`.
You do *not* need to set up a database or any interactivity on the webpage yet. Instructions for that will come later in the course!
```bash
go build -o notely && ./notely
```
## 🔹 2. Setup Github workflow CI
- Create a new branch ( `addtest` )
- Do some change & Create a PR
- In same branch - setup github workflow
	- init CI by creating the .github file system
	```shell
	mkdir .github .github/workflows && touch .github/workflows/ci.yml
	```
	- init tests ( currently forcing to fail for demo purposes )
	```sh
	echo "name: ci

on:
  pull_request:
    branches: [main]

jobs:
  tests:
    name: Tests
    runs-on: ubuntu-latest

    steps:
      - name: Check out code
        uses: actions/checkout@v4

      - name: Set up Go
        uses: actions/setup-go@v5
        with:
          go-version: '1.23.0'

      - name: Force Failure
        run: (exit 1)" >> .github/workflows/ci.yml

	```
	- commit then push the updates on repo
	- a new test is set ( which will fail ) to demo
	the automation running
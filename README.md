### Overview

- `Express.js`, `Typescript`, `node-config`,`ajv`, `Typebox`
- `Mocha`, `should.js`

### Installation

- Clone from GitHub
- Create file `local-development.js` inside `config` folder.
- Ask your admin/peers for the content of this file
- run `npm install`

### Information

The file `local-development.js` is used to store changes to config that is unique to your development environment, and
is also used to store secrets that should be not be committed to GitHub. By default, this file is added to `.gitignore`
More information about configuration can be found
here https://github.com/node-config/node-config/wiki/Configuration-Files

### Development

- `npm run dev` Start the development environment

### Benchmark

- `npm run benchmark` Running benchmark and produce report

### Proxies

- to proxy a single route:
  - `app.get('/users', proxy(baseUrl));` =>`baseUrl/users`
- to proxy a single route, different path:
  - `app.get('/users', proxy(baseUrl, {path:'orgs'}));`=> `baseUrl/orgs`
- to proxy a group of requests:
  - `app.all('/users/*', proxy(baseUrl));`=> `baseUrl/users/*`
- to proxy and replace the base,
  - `app.use('/users', Router().all('/listings',proxy(baseUrl)));`=> `baseUrl/listings`
  - or `app.all('/users/listings/*', proxy(baseUrl, {path: (req) => req.url.replace('/users','');`

### How to contribute

We use commitizen https://github.com/commitizen/cz-cli to standardize our commit messages

- `cz` : To commit
- `cz --retry`: There will be times when the pre-commit hook fails after `cz`. Use this command to avoid typing the last
  commitizen message

### How to add tests

Each additional or changed route should be accompanied by a test. The test is a simple acceptance test to ensure the API
call is proxied to the correct endpoint.

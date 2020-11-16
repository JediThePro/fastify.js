# <code>Fastify.js</code>

An efficient server implies a lower cost of the infrastructure, a better responsiveness under load and happy users.
How can you efficiently handle the resources of your server, knowing that you are serving the highest number of requests as possible, without sacrificing security validations and handy development?

Fastify.js is a web framework highly focused on providing the best developer experience with the least overhead and a powerful plugin architecture. It is inspired by Hapi and Express and as far as we know, it is one of the fastest web frameworks in town.

### Requirements

Node.js v10 LTS (10.16.0) or later.

### Quick start

Create a folder and make it your current working directory:

```
mkdir my-app
cd my-app
```

Generate a fastify project with `npm init`:

```sh
npm init fastify.js
```

Install dependencies:

```js
npm install
```

To start the app in dev mode:

```sh
npm run dev
```

For production mode:

```sh
npm start
```

Under the hood `npm init` downloads and runs **Fastify Create**
which in turn uses the generate functionality of **Fastify CLI**.


### Installation

If installing in an existing project, then Fastify can be installed into the project as a dependency:

Install with npm:
```
npm i fastify.js --save
```
Install with yarn:
```
yarn add fastify.js
```

### Example

```js
// Require the framework and instantiate it
const fastify = require('fastify.js')({
  logger: true
})

// Declare a route
fastify.get('/', (request, reply) => {
  reply.send({ hello: 'world' })
})

// Run the server!
fastify.listen(3000, (err, address) => {
  if (err) throw err
  fastify.log.info(`server listening on ${address}`)
})
```

with async-await:

```js
const fastify = require('fastify.js')({
  logger: true
})

fastify.get('/', async (request, reply) => {
  reply.type('application/json').code(200)
  return { hello: 'world' }
})

fastify.listen(3000, (err, address) => {
  if (err) throw err
  fastify.log.info(`server listening on ${address}`)
})
```

Do you want to know more? Head to the **<a href="./docs/Getting-Started.md"><code><b>Getting Started</b></code></a>**.

> ## Note
> `.listen` binds to the local host, `localhost`, interface by default (`127.0.0.1` or `::1`, depending on the operating system configuration). If you are running Fastify in a container (Docker, [GCP](https://cloud.google.com/), etc.), you may need to bind to `0.0.0.0`. Be careful when deciding to listen on all interfaces; it comes with inherent [security risks](https://web.archive.org/web/20170711105010/https://snyk.io/blog/mongodb-hack-and-secure-defaults/).
> See [the documentation](./docs/Server.md#listen) for more information.

### Core features

- **Highly performant:** as far as we know, Fastify is one of the fastest web frameworks in town, depending on the code complexity we can serve up to 76+ thousand requests per second.
- **Extendible:** Fastify is fully extensible via its hooks, plugins and decorators.
- **Schema based:** even if it is not mandatory we recommend to use [JSON Schema](http://json-schema.org/) to validate your routes and serialize your outputs, internally Fastify compiles the schema in a highly performant function.
- **Logging:** logs are extremely important but are costly; we chose the best logger to almost remove this cost, [Pino](https://github.com/pinojs/pino)!
- **Developer friendly:** the framework is built to be very expressive and help the developer in their daily use, without sacrificing performance and security.

### Benchmarks

__Machine:__ EX41S-SSD, Intel Core i7, 4Ghz, 64GB RAM, 4C/8T, SSD.

__Method:__: `autocannon -c 100 -d 40 -p 10 localhost:3000` * 2, taking the second average

| Framework          | Version                    | Router?      |  Requests/sec |
| :----------------- | :------------------------- | :----------: | ------------: |
| Express            | 4.17.1                     | &#10003;     | 15,978        |
| hapi               | 19.1.0                     | &#10003;     | 45,815        |
| Restify            | 8.5.1                      | &#10003;     | 49,279        |
| Koa                | 2.13.0                     | &#10007;     | 54,848        |
| **Fastify**        | **3.0.0**                  | **&#10003;** | **78,956**    |
| -                  |                            |              |               |
| `http.Server`      | 12.18.2	                  | &#10007;     | 70,380        |

Benchmarks taken using https://github.com/fastify/benchmarks. This is a
synthetic, "hello world" benchmark that aims to evaluate the framework
overhead. The overhead that each framework has on your application
depends on your application, you should __always__ benchmark if performance
matters to you.

## Documentation
* <a href="./docs/Getting-Started.md"><code><b>Getting Started</b></code></a>
* <a href="./docs/Server.md"><code><b>Server</b></code></a>
* <a href="./docs/Routes.md"><code><b>Routes</b></code></a>
* <a href="./docs/Logging.md"><code><b>Logging</b></code></a>
* <a href="./docs/Middleware.md"><code><b>Middleware</b></code></a>
* <a href="./docs/Hooks.md"><code><b>Hooks</b></code></a>
* <a href="./docs/Decorators.md"><code><b>Decorators</b></code></a>
* <a href="./docs/Validation-and-Serialization.md"><code><b>Validation and Serialization</b></code></a>
* <a href="./docs/Fluent-Schema.md"><code><b>Fluent Schema</b></code></a>
* <a href="./docs/Lifecycle.md"><code><b>Lifecycle</b></code></a>
* <a href="./docs/Reply.md"><code><b>Reply</b></code></a>
* <a href="./docs/Request.md"><code><b>Request</b></code></a>
* <a href="./docs/Errors.md"><code><b>Errors</b></code></a>
* <a href="./docs/ContentTypeParser.md"><code><b>Content Type Parser</b></code></a>
* <a href="./docs/Plugins.md"><code><b>Plugins</b></code></a>
* <a href="./docs/Testing.md"><code><b>Testing</b></code></a>
* <a href="./docs/Benchmarking.md"><code><b>Benchmarking</b></code></a>
* <a href="./docs/Write-Plugin.md"><code><b>How to write a good plugin</b></code></a>
* <a href="./docs/Plugins-Guide.md"><code><b>Plugins Guide</b></code></a>
* <a href="./docs/HTTP2.md"><code><b>HTTP2</b></code></a>
* <a href="./docs/LTS.md"><code><b>Long Term Support</b></code></a>
* <a href="./docs/TypeScript.md"><code><b>TypeScript and types support</b></code></a>
* <a href="./docs/Serverless.md"><code><b>Serverless</b></code></a>
* <a href="./docs/Recommendations.md"><code><b>Recommendations</b></code></a>

<!--


   SSSSSSSSSSSSSSS TTTTTTTTTTTTTTTTTTTTTTT     OOOOOOOOO     PPPPPPPPPPPPPPPPP
 SS:::::::::::::::ST:::::::::::::::::::::T   OO:::::::::OO   P::::::::::::::::P
S:::::SSSSSS::::::ST:::::::::::::::::::::T OO:::::::::::::OO P::::::PPPPPP:::::P
S:::::S     SSSSSSST:::::TT:::::::TT:::::TO:::::::OOO:::::::OPP:::::P     P:::::P
S:::::S            TTTTTT  T:::::T  TTTTTTO::::::O   O::::::O  P::::P     P:::::P
S:::::S                    T:::::T        O:::::O     O:::::O  P::::P     P:::::P
 S::::SSSS                 T:::::T        O:::::O     O:::::O  P::::PPPPPP:::::P
  SS::::::SSSSS            T:::::T        O:::::O     O:::::O  P:::::::::::::PP
    SSS::::::::SS          T:::::T        O:::::O     O:::::O  P::::PPPPPPPPP
       SSSSSS::::S         T:::::T        O:::::O     O:::::O  P::::P
            S:::::S        T:::::T        O:::::O     O:::::O  P::::P
            S:::::S        T:::::T        O::::::O   O::::::O  P::::P
SSSSSSS     S:::::S      TT:::::::TT      O:::::::OOO:::::::OPP::::::PP
S::::::SSSSSS:::::S      T:::::::::T       OO:::::::::::::OO P::::::::P
S:::::::::::::::SS       T:::::::::T         OO:::::::::OO   P::::::::P
 SSSSSSSSSSSSSSS         TTTTTTTTTTT           OOOOOOOOO     PPPPPPPPPP


 Do not edit this file directly. It is generally programatically by `jsdoc2md`

 If you'd like to make a change to the docs, do so by editing the comments in the source code.

 Pull requests for changes to this file will be rejected!

-->
# Contents

## Modules

<dl>
<dt><a href="#module_faktory">faktory</a></dt>
<dd><p>creates faktory singletons</p>
</dd>
</dl>

## Classes

<dl>
<dt><a href="#Client">Client</a></dt>
<dd><p>A client connection handle for interacting with the faktory server. Holds a pool of 1 or more
underlying connections. Safe for concurrent use and tolerant of unexpected
connection terminations. Use this object for all interactions with the factory server.</p>
</dd>
<dt><a href="#Job">Job</a></dt>
<dd><p>A class wrapping a <a href="#JobPayload">JobPayload</a></p>
<p>Creating and pushing a job is typically accomplished by using
a faktory client, which implements <code>.job</code> and automatically
sets the client for the job when calling <code>.push</code> on the job later.</p>
<p>You do not need to use this class directly.`</p>
</dd>
<dt><a href="#Mutation">Mutation</a></dt>
<dd><p>A wrapper for the <a href="https://github.com/contribsys/faktory/wiki/Mutate-API">Mutate API</a></p>
<p>A low-level data management API to script certain repairs or migrations.</p>
<p>!!! Please be warned: MUTATE commands can be slow and/or resource intensive.
<strong>They should not be used as part of your application logic.</strong></p>
</dd>
<dt><a href="#Worker">Worker</a></dt>
<dd><p>Representation of a worker process with many concurrent job processors. Works at the
concurrency set in options during construction. Will hold at most <code>concurrency</code> jobs
in-memory while processing at any one time. Listens for signals to quiet or shutdown.
Should not be started more than once per-process, nor should more than one worker be
started per-process.</p>
</dd>
</dl>

## Typedefs

<dl>
<dt><a href="#HI">HI</a> : <code>object</code></dt>
<dd><p>An after-connect initial message from the server to handshake the connection</p>
</dd>
<dt><a href="#JobFunction">JobFunction</a> : <code>function</code></dt>
<dd><p>A function that executes work</p>
</dd>
<dt><a href="#Jobtype">Jobtype</a> : <code>string</code></dt>
<dd><p>Discriminator used by a worker to decide how to execute a job. This will be the name you
used during register.</p>
</dd>
<dt><a href="#JobFunction">JobFunction</a> : <code>function</code></dt>
<dd><p>A function that executes work</p>
</dd>
<dt><a href="#Registry">Registry</a> : <code>Object.&lt;Jobtype, JobFunction&gt;</code></dt>
<dd><p>A lookup table holding the jobtype constants mapped to their job functions</p>
</dd>
<dt><a href="#ContextProvider">ContextProvider</a> : <code>function</code></dt>
<dd><p>A function returned by a job function that will be called with the job context as its
only argument and awaited. This exists to allow you to define simple job functions that
only accept their job args, but in many cases you might need the job&#39;s custom properties
or stateful connections (like a database connection) in your job and want to attach
a connection for your job function to use without having to create it itself.</p>
</dd>
<dt><a href="#Context">Context</a> : <code>object</code></dt>
<dd><p>A context object passed through middleware and to a job thunk</p>
</dd>
<dt><a href="#ContextProvider">ContextProvider</a> : <code>function</code></dt>
<dd><p>A function returned by a job function that will be called with the job context as its
only argument and awaited. This exists to allow you to define simple job functions that
only accept their job args, but in many cases you might need the job&#39;s custom properties
or stateful connections (like a database connection) in your job and want to attach
a connection for your job function to use without having to create it itself.</p>
</dd>
<dt><a href="#HELLO">HELLO</a> : <code>object</code></dt>
<dd><p>The client&#39;s response to the server&#39;s <a href="#HI">HI</a> to initiate a connection</p>
</dd>
<dt><a href="#JobPayload">JobPayload</a> : <code>Object</code></dt>
<dd><p>A work unit that can be scheduled by the faktory work server and executed by clients</p>
</dd>
<dt><a href="#RejectedJobFromPushBulk">RejectedJobFromPushBulk</a> : <code>Object</code></dt>
<dd><p>A lookup table holding the jobtype constants mapped to their job functions</p>
</dd>
<dt><a href="#RejectedJobsFromPushBulk">RejectedJobsFromPushBulk</a> : <code>Array</code></dt>
<dd><p>A lookup table holding the jobtype constants mapped to their job functions</p>
</dd>
<dt><a href="#RFC3339_DateTime">RFC3339_DateTime</a> : <code>string</code></dt>
<dd><p>An RFC3339-format datetime string</p>
</dd>
</dl>

# API

<a name="module_faktory"></a>

## faktory
creates faktory singletons


* [faktory](#module_faktory)
    * [.use(fn)](#module_faktory+use) ⇒ <code>FaktoryControl</code>
    * [.register(name, fn)](#module_faktory+register) ⇒ <code>FaktoryControl</code>
    * [.connect(...args)](#module_faktory+connect) ⇒ [<code>Client</code>](#Client)
    * [.work(options)](#module_faktory+work) ⇒ <code>Promise</code>
    * [.stop()](#module_faktory+stop) ⇒ <code>promise</code>

<a name="module_faktory+use"></a>

### faktory.use(fn) ⇒ <code>FaktoryControl</code>
Adds a middleware function to the stack

**Kind**: instance method of [<code>faktory</code>](#module_faktory)  
**Returns**: <code>FaktoryControl</code> - this  
**See**: [koa middleware](https://github.com/koajs/koa/blob/master/docs/guide.md#writing-middleware)  

| Param | Type | Description |
| --- | --- | --- |
| fn | <code>function</code> | koa-compose-style middleware function |

**Example**  
```js
faktory.use(async (ctx, next) => {
  // a pool you created to hold database connections
  pool.use(async (conn) => {
    ctx.db = conn;
    await next();
  });
});
```
<a name="module_faktory+register"></a>

### faktory.register(name, fn) ⇒ <code>FaktoryControl</code>
Adds a [JobFunction](#JobFunction) to the [Registry](#Registry)

**Kind**: instance method of [<code>faktory</code>](#module_faktory)  
**Returns**: <code>FaktoryControl</code> - this  

| Param | Type | Description |
| --- | --- | --- |
| name | [<code>Jobtype</code>](#Jobtype) | string descriptor for the jobtype |
| fn | [<code>JobFunction</code>](#JobFunction) |  |

**Example**  
```js
faktory.register('MyJob', (...args) => {
  // some work
});
```
<a name="module_faktory+connect"></a>

### faktory.connect(...args) ⇒ [<code>Client</code>](#Client)
Creates a new [Client](#Client)

**Kind**: instance method of [<code>faktory</code>](#module_faktory)  

| Param | Type | Description |
| --- | --- | --- |
| ...args | <code>\*</code> | args forwarded to [Client](#Client) |

**Example**  
```js
const client = await faktory.connect();

await client.push(job);
```
<a name="module_faktory+work"></a>

### faktory.work(options) ⇒ <code>Promise</code>
Starts a worker. Resolves after the worker is started. Only call this
once per-process.

**Kind**: instance method of [<code>faktory</code>](#module_faktory)  
**Returns**: <code>Promise</code> - the [Worker.work](Worker.work) promise  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>object</code> | options to [Worker](#Worker) |

**Example**  
```js
// this keeps the process open and can be `await`ed
faktory.work();
```
<a name="module_faktory+stop"></a>

### faktory.stop() ⇒ <code>promise</code>
Stops the worker previously started.

**Kind**: instance method of [<code>faktory</code>](#module_faktory)  
**Returns**: <code>promise</code> - promise returned by [Worker.stop](Worker.stop)  
**Example**  
```js
// previously
faktory.work();

faktory.stop();
```
<a name="Client"></a>

## Client
A client connection handle for interacting with the faktory server. Holds a pool of 1 or more
underlying connections. Safe for concurrent use and tolerant of unexpected
connection terminations. Use this object for all interactions with the factory server.

**Kind**: global class  

* [Client](#Client)
    * [new Client([options])](#new_Client_new)
    * [.connect()](#Client+connect) ⇒ [<code>Promise.&lt;Client&gt;</code>](#Client)
    * [.close()](#Client+close) ⇒ <code>Promise.&lt;undefined&gt;</code>
    * [.job(jobtype, ...args)](#Client+job) ⇒ [<code>Job</code>](#Job)
    * [.send(...args)](#Client+send)
    * [.fetch(...queues)](#Client+fetch) ⇒ <code>Promise.&lt;(object\|null)&gt;</code>
    * [.beat()](#Client+beat) ⇒ <code>Promise.&lt;string&gt;</code>
    * [.push(job)](#Client+push) ⇒ <code>Promise.&lt;string&gt;</code>
    * [.pushBulk(jobs)](#Client+pushBulk) ⇒ [<code>Promise.&lt;RejectedJobsFromPushBulk&gt;</code>](#RejectedJobsFromPushBulk)
    * [.flush()](#Client+flush) ⇒ <code>Promise.&lt;string&gt;</code>
    * [.info()](#Client+info) ⇒ <code>Promise.&lt;object&gt;</code>
    * [.ack(jid)](#Client+ack) ⇒ <code>Promise.&lt;string&gt;</code>
    * [.fail(jid, e)](#Client+fail) ⇒ <code>Promise.&lt;string&gt;</code>

<a name="new_Client_new"></a>

### new Client([options])
Creates a Client with a connection pool


| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [options] | <code>object</code> |  |  |
| [options.url] | <code>string</code> | <code>&quot;tcp://localhost:7419&quot;</code> | connection string for the faktory server                                                    (checks for FAKTORY_PROVIDER and                                                    FAKTORY_URL) |
| [options.host] | <code>string</code> | <code>&quot;localhost&quot;</code> | host string to connect to |
| [options.port] | <code>number</code> \| <code>string</code> | <code>7419</code> | port to connect to faktory server on |
| [options.password] | <code>string</code> |  | faktory server password to use during HELLO |
| [options.wid] | <code>string</code> |  | optional wid that should be provided to the server                               (only necessary for a worker process consuming jobs) |
| [options.labels] | <code>Array.&lt;string&gt;</code> | <code>[]</code> | optional labels to provide the faktory server                                       for this client |
| [options.poolSize] | <code>number</code> | <code>10</code> | the maxmimum size of the connection pool |

**Example**  
```js
const client = new Client();

const job = await client.fetch('default');
```
<a name="Client+connect"></a>

### client.connect() ⇒ [<code>Promise.&lt;Client&gt;</code>](#Client)
Explicitly opens a connection and then closes it to test connectivity.
Under normal circumstances you don't need to call this method as all of the
communication methods will check out a connection before executing. If a connection is
not available, one will be created. This method exists to ensure connection is possible
if you need to do so. You can think of this like [sqlx#MustConnect](https://godoc.org/github.com/jmoiron/sqlx#MustConnect)

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: [<code>Promise.&lt;Client&gt;</code>](#Client) - resolves when a connection is opened  
<a name="Client+close"></a>

### client.close() ⇒ <code>Promise.&lt;undefined&gt;</code>
Closes the connection to the server

**Kind**: instance method of [<code>Client</code>](#Client)  
<a name="Client+job"></a>

### client.job(jobtype, ...args) ⇒ [<code>Job</code>](#Job)
Creates a new Job object to build a job payload

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: [<code>Job</code>](#Job) - a job builder with attached Client for PUSHing  
**See**: Job  

| Param | Type | Description |
| --- | --- | --- |
| jobtype | <code>String</code> | name of the job function |
| ...args | <code>\*</code> | arguments to the job function |

<a name="Client+send"></a>

### client.send(...args)
Borrows a connection from the connection pool, forwards all arguments to
[Connection.send](Connection.send), and checks the connection back into the pool when
the promise returned by the wrapped function is resolved or rejected.

**Kind**: instance method of [<code>Client</code>](#Client)  
**See**: Connection.send  

| Param | Type | Description |
| --- | --- | --- |
| ...args | <code>\*</code> | arguments to [Connection.send](Connection.send) |

<a name="Client+fetch"></a>

### client.fetch(...queues) ⇒ <code>Promise.&lt;(object\|null)&gt;</code>
Fetches a job payload from the server from one of ...queues

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: <code>Promise.&lt;(object\|null)&gt;</code> - a job payload if one is available, otherwise null  

| Param | Type | Description |
| --- | --- | --- |
| ...queues | <code>String</code> | list of queues to pull a job from |

<a name="Client+beat"></a>

### client.beat() ⇒ <code>Promise.&lt;string&gt;</code>
Sends a heartbeat for this.wid to the server

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: <code>Promise.&lt;string&gt;</code> - string 'OK' when the heartbeat is accepted, otherwise
                          may return a state string when the server has a signal
                          to send this client (`quiet`, `terminate`)  
<a name="Client+push"></a>

### client.push(job) ⇒ <code>Promise.&lt;string&gt;</code>
Pushes a job payload to the server

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: <code>Promise.&lt;string&gt;</code> - the jid for the pushed job  

| Param | Type | Description |
| --- | --- | --- |
| job | [<code>Job</code>](#Job) \| <code>Object</code> | job payload to push |

<a name="Client+pushBulk"></a>

### client.pushBulk(jobs) ⇒ [<code>Promise.&lt;RejectedJobsFromPushBulk&gt;</code>](#RejectedJobsFromPushBulk)
Pushes multiple jobs to the server and return map containing failed job submissions if any

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: [<code>Promise.&lt;RejectedJobsFromPushBulk&gt;</code>](#RejectedJobsFromPushBulk) - response from the faktory server  

| Param | Type | Description |
| --- | --- | --- |
| jobs | [<code>Array.&lt;Job&gt;</code>](#Job) \| <code>Array.&lt;Object&gt;</code> | jobs payload to push |

<a name="Client+flush"></a>

### client.flush() ⇒ <code>Promise.&lt;string&gt;</code>
Sends a FLUSH to the server

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: <code>Promise.&lt;string&gt;</code> - resolves with the server's response text  
<a name="Client+info"></a>

### client.info() ⇒ <code>Promise.&lt;object&gt;</code>
Sends an INFO command to the server

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: <code>Promise.&lt;object&gt;</code> - the server's INFO response object  
<a name="Client+ack"></a>

### client.ack(jid) ⇒ <code>Promise.&lt;string&gt;</code>
Sends an ACK to the server for a particular job ID

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: <code>Promise.&lt;string&gt;</code> - the server's response text  

| Param | Type | Description |
| --- | --- | --- |
| jid | <code>String</code> | the jid of the job to acknowledge |

<a name="Client+fail"></a>

### client.fail(jid, e) ⇒ <code>Promise.&lt;string&gt;</code>
Sends a FAIL command to the server for a particular job ID with error information

**Kind**: instance method of [<code>Client</code>](#Client)  
**Returns**: <code>Promise.&lt;string&gt;</code> - the server's response text  

| Param | Type | Description |
| --- | --- | --- |
| jid | <code>String</code> | the jid of the job to FAIL |
| e | <code>Error</code> | an error object that caused the job to fail |

<a name="Job"></a>

## Job
A class wrapping a [JobPayload](#JobPayload)

Creating and pushing a job is typically accomplished by using
a faktory client, which implements `.job` and automatically
sets the client for the job when calling `.push` on the job later.

You do not need to use this class directly.`

**Kind**: global class  

* [Job](#Job)
    * [new Job(jobtype, [client])](#new_Job_new)
    * _instance_
        * [.jid](#Job+jid)
        * [.queue](#Job+queue)
        * [.args](#Job+args)
        * [.priority](#Job+priority)
        * [.retry](#Job+retry)
        * [.at](#Job+at)
        * [.reserveFor](#Job+reserveFor)
        * [.custom](#Job+custom)
        * [.toJSON()](#Job+toJSON) ⇒ <code>object</code>
        * [.push()](#Job+push) ⇒ <code>string</code>
    * _static_
        * [.jid()](#Job.jid) ⇒ <code>string</code>

<a name="new_Job_new"></a>

### new Job(jobtype, [client])
Creates a job


| Param | Type | Description |
| --- | --- | --- |
| jobtype | <code>string</code> | [Jobtype](#Jobtype) string |
| [client] | [<code>Client</code>](#Client) | a client to use for communicating to the server (if calling push) |

**Example** *(with a faktory client)*  
```js
// with a client
const client = await faktory.connect();
const job = client.job('SendWelcomeEmail', id);
```
<a name="Job+jid"></a>

### job.jid
sets the jid

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>string</code> | the >8 length jid |

<a name="Job+queue"></a>

### job.queue
sets the queue

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>string</code> | queue name |

<a name="Job+args"></a>

### job.args
sets the args

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>Array</code> | array of positional arguments |

<a name="Job+priority"></a>

### job.priority
sets the priority of this job

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>number</code> | 0-9 |

<a name="Job+retry"></a>

### job.retry
sets the retry count

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>number</code> | {@see JobPayload} |

<a name="Job+at"></a>

### job.at
sets the scheduled time

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>Date</code> \| <code>string</code> | the date object or RFC3339 timestamp string |

<a name="Job+reserveFor"></a>

### job.reserveFor
sets the reserveFor parameter

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type |
| --- | --- |
| value | <code>number</code> | 

<a name="Job+custom"></a>

### job.custom
sets the custom object property

**Kind**: instance property of [<code>Job</code>](#Job)  
**See**: JobPayload  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>object</code> | the custom data |

<a name="Job+toJSON"></a>

### job.toJSON() ⇒ <code>object</code>
Generates an object from this instance for transmission over the wire

**Kind**: instance method of [<code>Job</code>](#Job)  
**Returns**: <code>object</code> - the job as a serializable javascript object  
**Link**: JobPayload|JobPayload}  
**See**: JobPayload  
<a name="Job+push"></a>

### job.push() ⇒ <code>string</code>
Pushes this job to the faktory server. Modifications after this point are not
persistable to the server

**Kind**: instance method of [<code>Job</code>](#Job)  
**Returns**: <code>string</code> - return of client.push(job)  
<a name="Job.jid"></a>

### Job.jid() ⇒ <code>string</code>
generates a uuid

**Kind**: static method of [<code>Job</code>](#Job)  
**Returns**: <code>string</code> - a uuid/v4 string  
<a name="Mutation"></a>

## Mutation
A wrapper for the [Mutate API](https://github.com/contribsys/faktory/wiki/Mutate-API)

A low-level data management API to script certain repairs or migrations.

!!! Please be warned: MUTATE commands can be slow and/or resource intensive.
**They should not be used as part of your application logic.**

**Kind**: global class  

* [Mutation](#Mutation)
    * [new Mutation(client)](#new_Mutation_new)
    * [.ofType(type)](#Mutation+ofType)
    * [.withJids(...jids)](#Mutation+withJids)
    * [.matching(pattern)](#Mutation+matching)
    * [.clear()](#Mutation+clear)
    * [.kill()](#Mutation+kill)
    * [.discard()](#Mutation+discard)
    * [.requeue()](#Mutation+requeue)

<a name="new_Mutation_new"></a>

### new Mutation(client)

| Param | Type |
| --- | --- |
| client | [<code>Client</code>](#Client) | 

<a name="Mutation+ofType"></a>

### mutation.ofType(type)
Filters the affected jobs by a jobtype string.
Use this to ensure you're only affecting a single jobtype if applicable.
Can be chained.

Note: jobtype and other filters do not apply for the *clear* command.

**Kind**: instance method of [<code>Mutation</code>](#Mutation)  

| Param | Type | Description |
| --- | --- | --- |
| type | <code>string</code> | jobtype fiter for operation |

**Example**  
```js
client.dead.ofType('SendEmail').discard();
```
<a name="Mutation+withJids"></a>

### mutation.withJids(...jids)
Filters the affected jobs by one or more job ids. This is much more
efficient when only one jid is provided. Can be chained.

Note: jobtype and other filters do not apply for the *clear* command.

**Kind**: instance method of [<code>Mutation</code>](#Mutation)  

| Param | Type | Description |
| --- | --- | --- |
| ...jids | <code>string</code> | job ids to target for the operation |

**Example**  
```js
await client.retries.withJids('1234').requeue();
```
<a name="Mutation+matching"></a>

### mutation.matching(pattern)
Filters the MUTATE selection to jobs matching a Redis SCAN pattern.
Can be chained.

Note the regexp filter scans the entire job payload and can be tricky to
get right, for instance you'll probably need * on both sides. The regexp
filter option is passed to Redis's SCAN command directly, read the SCAN
documentation for further details.
https://redis.io/commands/scan

**Kind**: instance method of [<code>Mutation</code>](#Mutation)  

| Param | Type | Description |
| --- | --- | --- |
| pattern | <code>string</code> | redis SCAN pattern to target jobs for the operation |

**Example**  
```js
await client.retries.matching("*uid:12345*").kill();
```
<a name="Mutation+clear"></a>

### mutation.clear()
Executes a *clear* mutation. This clears the
set entirely **and any filtering added does not apply**.

**Kind**: instance method of [<code>Mutation</code>](#Mutation)  
<a name="Mutation+kill"></a>

### mutation.kill()
Executes a *kill* mutation. Jobs that are killed are sent to the dead set.

**Kind**: instance method of [<code>Mutation</code>](#Mutation)  
<a name="Mutation+discard"></a>

### mutation.discard()
Executes a *discard* mutation. Jobs that are discarded are permanently deleted.

**Kind**: instance method of [<code>Mutation</code>](#Mutation)  
<a name="Mutation+requeue"></a>

### mutation.requeue()
Executes a *requeue* mutation. Jobs that are requeued are sent back to their
original queue for processing.

**Kind**: instance method of [<code>Mutation</code>](#Mutation)  
<a name="Worker"></a>

## Worker
Representation of a worker process with many concurrent job processors. Works at the
concurrency set in options during construction. Will hold at most `concurrency` jobs
in-memory while processing at any one time. Listens for signals to quiet or shutdown.
Should not be started more than once per-process, nor should more than one worker be
started per-process.

**Kind**: global class  

* [Worker](#Worker)
    * [new Worker([options])](#new_Worker_new)
    * [.work()](#Worker+work) ⇒
    * [.quiet()](#Worker+quiet)
    * [.stop()](#Worker+stop) ⇒ <code>promise</code>
    * [.beat()](#Worker+beat)
    * [.use(fn)](#Worker+use) ⇒ <code>FaktoryControl</code>
    * [.register(name, fn)](#Worker+register) ⇒ <code>FaktoryControl</code>

<a name="new_Worker_new"></a>

### new Worker([options])

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [options] | <code>object</code> |  |  |
| [options.wid] | <code>String</code> | <code>uuid().slice(0, 8)</code> | the wid the worker will use |
| [options.concurrency] | <code>Number</code> | <code>20</code> | how many jobs this worker can process at once |
| [options.shutdownTimeout] | <code>Number</code> | <code>8</code> | the amount of time in seconds that the worker                                             may take to finish a job before exiting                                             ungracefully |
| [options.beatInterval] | <code>Number</code> | <code>15</code> | the amount of time in seconds between each                                             heartbeat |
| [options.queues] | <code>Array.&lt;string&gt;</code> | <code>[&#x27;default&#x27;]</code> | the queues this worker will fetch jobs from |
| [options.middleware] | <code>Array.&lt;function()&gt;</code> | <code>[]</code> | a set of middleware to run before performing                                               each job                                       in koa.js-style middleware execution signature |
| [options.registry] | [<code>Registry</code>](#Registry) | <code>Registry</code> | the job registry to use when working |
| [options.poolSize] | <code>Number</code> | <code>concurrency+2</code> | the client connection pool size for                                                  this worker |

**Example**  
```js
const worker = new Worker({
  queues: ['critical', 'default', 'low'],
});

worker.work();
```
<a name="Worker+work"></a>

### worker.work() ⇒
starts the worker fetch loop and job processing

**Kind**: instance method of [<code>Worker</code>](#Worker)  
**Returns**: self, when working has been stopped by a signal or concurrent
                       call to stop or quiet  
**See**

- Worker.quiet
- Worker.stop

<a name="Worker+quiet"></a>

### worker.quiet()
Signals to the worker to discontinue fetching new jobs and allows the worker
to continue processing any currently-running jobs

**Kind**: instance method of [<code>Worker</code>](#Worker)  
<a name="Worker+stop"></a>

### worker.stop() ⇒ <code>promise</code>
stops the worker

**Kind**: instance method of [<code>Worker</code>](#Worker)  
**Returns**: <code>promise</code> - resolved when worker stops  
<a name="Worker+beat"></a>

### worker.beat()
Sends a heartbeat for this server and interprets the response state (if present)
to quiet or terminate the worker

**Kind**: instance method of [<code>Worker</code>](#Worker)  
<a name="Worker+use"></a>

### worker.use(fn) ⇒ <code>FaktoryControl</code>
Adds a middleware function to the stack

**Kind**: instance method of [<code>Worker</code>](#Worker)  
**Returns**: <code>FaktoryControl</code> - this  
**See**: [koa middleware](https://github.com/koajs/koa/blob/master/docs/guide.md#writing-middleware)  

| Param | Type | Description |
| --- | --- | --- |
| fn | <code>function</code> | koa-compose-style middleware function |

**Example**  
```js
faktory.use(async (ctx, next) => {
  // a pool you created to hold database connections
  pool.use(async (conn) => {
    ctx.db = conn;
    await next();
  });
});
```
<a name="Worker+register"></a>

### worker.register(name, fn) ⇒ <code>FaktoryControl</code>
Adds a [JobFunction](#JobFunction) to the [Registry](#Registry)

**Kind**: instance method of [<code>Worker</code>](#Worker)  
**Returns**: <code>FaktoryControl</code> - this  

| Param | Type | Description |
| --- | --- | --- |
| name | [<code>Jobtype</code>](#Jobtype) | string descriptor for the jobtype |
| fn | [<code>JobFunction</code>](#JobFunction) |  |

**Example**  
```js
faktory.register('MyJob', (...args) => {
  // some work
});
```
<a name="HI"></a>

## HI : <code>object</code>
An after-connect initial message from the server to handshake the connection

**Kind**: global typedef  
**See**: HELLO  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| v | <code>number</code> | faktory server protocol version number |
| i | <code>number</code> | only present when password is required. number of password hash iterations.                      see [HELLO](#HELLO). |
| s | <code>string</code> | only present when password is required. salt for password hashing.                      see [HELLO](#HELLO). |

<a name="JobFunction"></a>

## JobFunction : <code>function</code>
A function that executes work

**Kind**: global typedef  

| Param | Type | Description |
| --- | --- | --- |
| ...args | <code>\*</code> | arguments from the job payload |

**Example**  
```js
function(...args) {
  // does something meaningful
}
```
<a name="Jobtype"></a>

## Jobtype : <code>string</code>
Discriminator used by a worker to decide how to execute a job. This will be the name you
used during register.

**Kind**: global typedef  
**See**: [https://github.com/contribsys/faktory/wiki/The-Job-Payload](https://github.com/contribsys/faktory/wiki/The-Job-Payload)  
**Example**  
```js
// where `MyFunction` is the jobtype

faktory.register('MyFunction', () => {})
```
<a name="JobFunction"></a>

## JobFunction : <code>function</code>
A function that executes work

**Kind**: global typedef  

| Param | Type | Description |
| --- | --- | --- |
| ...args | <code>\*</code> | arguments from the job payload |

**Example**  
```js
function(...args) {
  // does something meaningful
}
```
<a name="Registry"></a>

## Registry : <code>Object.&lt;Jobtype, JobFunction&gt;</code>
A lookup table holding the jobtype constants mapped to their job functions

**Kind**: global typedef  
**See**

- Jobtype
- JobFunction

**Example**  
```js
{
  SendWelcomeUser: (id) => {
    // job fn
  },
  GenerateThumbnail: (id, size) => {
    // job fn
  }
}
```
<a name="ContextProvider"></a>

## ContextProvider : <code>function</code>
A function returned by a job function that will be called with the job context as its
only argument and awaited. This exists to allow you to define simple job functions that
only accept their job args, but in many cases you might need the job's custom properties
or stateful connections (like a database connection) in your job and want to attach
a connection for your job function to use without having to create it itself.

**Kind**: global typedef  
**See**: Context  

| Param | Type | Description |
| --- | --- | --- |
| ctx | <code>object</code> | context object containing the job and any other data attached                     via userland-middleware |

**Example**  
```js
// assumes you have middleware that attaches `db` to `ctx`

faktory.register('UserWelcomer', (...args) => async (ctx) => {
  const [ id ] = args;
  const user = await ctx.db.users.find(id);
  const email = new WelcomeEmail(user);
  await email.deliver();
});
```
<a name="Context"></a>

## Context : <code>object</code>
A context object passed through middleware and to a job thunk

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| Context.job | <code>object</code> | the job payload |
| Context.fn | <code>function</code> | a reference to the job function |

<a name="ContextProvider"></a>

## ContextProvider : <code>function</code>
A function returned by a job function that will be called with the job context as its
only argument and awaited. This exists to allow you to define simple job functions that
only accept their job args, but in many cases you might need the job's custom properties
or stateful connections (like a database connection) in your job and want to attach
a connection for your job function to use without having to create it itself.

**Kind**: global typedef  
**See**: Context  

| Param | Type | Description |
| --- | --- | --- |
| ctx | <code>object</code> | context object containing the job and any other data attached                     via userland-middleware |

**Example**  
```js
// assumes you have middleware that attaches `db` to `ctx`

faktory.register('UserWelcomer', (...args) => async (ctx) => {
  const [ id ] = args;
  const user = await ctx.db.users.find(id);
  const email = new WelcomeEmail(user);
  await email.deliver();
});
```
<a name="HELLO"></a>

## HELLO : <code>object</code>
The client's response to the server's [HI](#HI) to initiate a connection

**Kind**: global typedef  
**See**

- HI
- [Faktory Protocol Specification](https://github.com/contribsys/faktory/blob/master/docs/protocol-specification.md)

**Properties**

| Name | Type | Description |
| --- | --- | --- |
| v | <code>string</code> | the faktory client protocol version |
| hostname | <code>string</code> | name of the host that is running this worker |
| wid | <code>string</code> | globally unique identifier for this worker |
| pid | <code>number</code> | local process identifier for this worker on its host |
| labels | <code>Array.&lt;string&gt;</code> | labels that apply to this worker, to allow producers to target work                             units to worker types. |
| pwdhash | <code>string</code> | This field should be the hexadecimal representation of the ith                            SHA256 hash of the client password concatenated with the value in s. |

<a name="JobPayload"></a>

## JobPayload : <code>Object</code>
A work unit that can be scheduled by the faktory work server and executed by clients

**Kind**: global typedef  
**See**

- [https://github.com/contribsys/faktory/wiki/The-Job-Payload](https://github.com/contribsys/faktory/wiki/The-Job-Payload)
- [Faktory Protocol Specification - Work Units](https://github.com/contribsys/faktory/blob/master/docs/protocol-specification.md#work-units)

**Properties**

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| [jid] | <code>string</code> | <code>&quot;uuid()&quot;</code> | globally unique ID for the job. |
| jobtype | [<code>Jobtype</code>](#Jobtype) |  |  |
| [queue] | <code>string</code> | <code>&quot;default&quot;</code> | which job queue to push this job onto. |
| [args] | <code>array</code> | <code>[]</code> | parameters the worker should use when executing the job. |
| [priority] | <code>number</code> | <code>5</code> | higher priority jobs are dequeued before lower priority jobs. |
| [retry] | <code>number</code> | <code>25</code> | number of times to retry this job if it fails. 0 discards the                               failed job, -1 saves the failed job to the dead set. |
| [at] | [<code>RFC3339\_DateTime</code>](#RFC3339_DateTime) |  | run the job at approximately this time; immediately if blank |
| [reserve_for] | <code>number</code> | <code>1800</code> | number of seconds a job may be held by a worker before it                                       is considered failed. |
| custom | <code>object</code> |  | provides additional context to the worker executing the job. |

<a name="RejectedJobFromPushBulk"></a>

## RejectedJobFromPushBulk : <code>Object</code>
A lookup table holding the jobtype constants mapped to their job functions

**Kind**: global typedef  
**See**: JobPayload  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| reason | <code>string</code> | server-provided reason for the job failing to enqueue. |
| jobPayload | [<code>JobPayload</code>](#JobPayload) | the job payload that failed to enqueue. |

<a name="RejectedJobsFromPushBulk"></a>

## RejectedJobsFromPushBulk : <code>Array</code>
A lookup table holding the jobtype constants mapped to their job functions

**Kind**: global typedef  
**See**

- RejectedJobFromPushBulk
- JobPayload

<a name="RFC3339_DateTime"></a>

## RFC3339\_DateTime : <code>string</code>
An RFC3339-format datetime string

**Kind**: global typedef  
**Example**  
```js
"2002-10-02T10:00:00-05:00"
"2002-10-02T15:00:00Z"
"2002-10-02T15:00:00.05Z"

new Date().toISOString();
// => '2019-02-11T15:59:15.593Z'
```

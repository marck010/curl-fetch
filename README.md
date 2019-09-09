## Motivation

First the difficulty was making http2 requests on node through an http1 proxy. Libcurl abstracts this for us. So why not curl? With this in mind, I decided to create a lib that uses background curl but with the fetch API syntax.

## Installing

To utilize for node.js install the the `npm` module:

```bash
npm i fetch-curl --save
```

## Common Usage

### Simple GET

```js
const res = await fetch('https://restcountries-v1.p.rapidapi.com/all');

const json = res.json();

console.log(json)
```

### POST

```js
const res = await fetch('https://foo/', {
        method: 'POST',
        body: {
            name: 'foo',
            email:'foo@foo.com'
        }
        headers: {
            'accept': 'application/json',
            'content-type': 'application/json',
        }
    });

const json = res.json();
```

#### Default Setings

```json
{
    verbose: false,
    method: 'GET',
    folow: 5,
    timeout: 60000,
    proxyType: 'https',
    useProxy: false,
    version: 2, // 1 - Http 1 | 2 - Http 1.1 | 3 - Http 2
    redirect: 'follow'
}
```

### All Options

```
{
  body?: any;
  headers?: Headers;
  method?: string;
  redirect?: RequestRedirect;
  proxy?: string;
  timeout?: number;
  follow?: number;
  verbose?: boolean;
  version?: number;
}

```
> body - Body request

> headers - Headers request

> method - Method Http

> redirect - To folow redirect 'follow'.

> proxy - Proxy Url

> timeout - Time out request

> follow - Max redirects

> verbose - Logs curl

> version - Http Version. Http1, Http1.1 Http2 Suported
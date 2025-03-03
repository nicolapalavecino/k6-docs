---
title: 'request(method, url, [body], [params])'
head_title: 'httpx.request()'
description: 'Generic method for making arbitrary HTTP requests'
excerpt: 'Generic method for making arbitrary HTTP requests'
---

Generic method for making arbitrary HTTP requests. 

Consider using specific methods for making common requests ([get](/javascript-api/jslib/httpx/get-url-body-params), [post](/javascript-api/jslib/httpx/post-url-body-params), [put](/javascript-api/jslib/httpx/put-url-body-params), [patch](/javascript-api/jslib/httpx/patch-url-body-params))


| Parameter      | Type   | Description                                                                          |
| -------------- | ------ | ------------------------------------------------------------------------------------ |
| method  | string    | HTTP method. Note, the method must be uppercase (GET, POST, PUT, PATCH, OPTIONS, HEAD, etc) |
| url  | string    | HTTP URL. If baseURL is set, provide only path. |
| body (optional) | null / string / object / ArrayBuffer / [SharedArray](/javascript-api/k6-data/sharedarray) | Request body; objects will be `x-www-form-urlencoded`. Set to `null` to omit the body. |
| params (optional) | null or object {} | Additional [parameters](/javascript-api/k6-http/params) for this specific request. |


### Returns

| Type                                         | Description           |
| -------------------------------------------- | --------------------- |
| [Response](/javascript-api/k6-http/response) | HTTP [Response](/javascript-api/k6-http/response) object. |


### Example

<CodeGroup labels={[]}>

```javascript
import { Httpx } from 'https://jslib.k6.io/httpx/0.0.4/index.js';

const session = new Httpx({
  baseURL: 'https://httpbin.test.k6.io',
  timeout: 20000, // 20s timeout.
});

export default function testSuite() {
  const resp_get = session.request('GET', `/status/200`);
  const resp_post = session.request('POST', `/status/200`, { key: 'value' });
  const resp_put = session.request('PUT', `/status/200`, { key: 'value' });
  const resp_patch = session.request('PATCH', `/status/200`, { key: 'value' });
  const resp_delete = session.request('DELETE', `/status/200`);
}
```

</CodeGroup>

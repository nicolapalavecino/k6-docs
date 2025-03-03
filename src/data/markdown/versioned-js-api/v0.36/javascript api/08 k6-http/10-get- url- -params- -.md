---
title: 'get( url, [params] )'
description: 'Issue an HTTP GET request.'
excerpt: 'Issue an HTTP GET request.'
---

Make a GET request.

| Parameter         | Type   | Description                                                                               |
| ----------------- | ------ | ----------------------------------------------------------------------------------------- |
| url               | string / [HTTP URL](/javascript-api/k6-http/url-url#returns) | Request URL (e.g. `http://example.com`).      |
| params (optional) | object | [Params](/javascript-api/k6-http/params) object containing additional request parameters. |

### Returns

| Type                                         | Description           |
| -------------------------------------------- | --------------------- |
| [Response](/javascript-api/k6-http/response) | HTTP Response object. |

### Example fetching a URL

<CodeGroup labels={[]}>

```javascript
import http from 'k6/http';

export default function () {
  const res = http.get('https://test.k6.io');
  console.log(JSON.stringify(res.headers));
}
```

</CodeGroup>

在 `uni-app` 的 `request` API 中，如果开发者在 GET 请求中将参数放在 `data` 字段中，`uni-app` 会自动将这些参数转换为查询字符串并附加到请求的 URL 上。这是 `uni-app` 为了简化开发而提供的特性，允许开发者以类似发送 POST 请求的方式处理 GET 请求的参数。

以下是 `uni-app` 中发送 GET 请求的代码示例：

```js
uni.request({
  url: 'https://example.com/api/data',  // 请注意，实际使用时应替换为有效的 URL
  method: 'GET',
  data: {
    param1: 'value1',
    param2: 'value2'
  },
  success: function(res) {
    console.log(res.data);
  },
  fail: function(err) {
    console.error(err);
  }
});
```

uni-app 将自动将请求转换为以下形式：

```js
https://example.com/api/data?param1=value1&param2=value2
```

这种方式确保了即使在 GET 请求中使用了 data 字段，参数也会被正确地附加到 URL 上，而不是作为请求体发送。

如果开发者不希望参数被转换为查询字符串，或者需要发送一个实际的请求体（例如使用 POST 方法），应在 uni.request 调用中明确指定 method 为 'POST' 或其他相应的 HTTP 方法，并在 data 字段中放置请求体参数。

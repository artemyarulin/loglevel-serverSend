<a name="loglevelLogServer"></a>
##loglevelLogServer(logger, options)
Extend loglevel with new plugin which will send log information to the log-sever. Send is async and all of the messages send one by one

| Param | Type | Description |
| ----- | ---- | ----------- |
| logger | <code>object</code> | loglevel instance to be extended |
| options | <code>object</code> |  |
| \[options.url=<code>&#x27;http://localhost:8000/main/log&#x27;</code>\] | <code>string</code> | Server url which would be used as a log server |
| \[options.prefix=<code>null</code>\] | <code>string</code> \| <code>function</code> | Prefix for all log messages. Either string or function wich should return string and accept log severity and message as parameters |
| \[options.callOriginal=<code>false</code>\] | <code>Bool</code> | If set to true - original loglevel method for logging would be called |

**Example**  
```js
loglevelLogServer(log,{url:'https://example.com/app/log',prefix: function(logSev,message) {
    return '[' + new Date().toISOString() + '] ' + logSev + ': ' + message + '\n'   
}})
```
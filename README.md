Plugin for JS logger [loglevel](https://github.com/pimterry/loglevel) which will forward all log messages to the server

# Features
- Send is async and wouldn't slow down the application
- Messages send one by one, so the order is maintained
- Any server which accept POST request should be supported
- You can specify prefix function which would dynamically add prefix for all log messages (app name, current user, etc.)

# Installation
- Using bower - `bower install loglevel-server-send`
- Manually - take [loglevel-serverSend.js](loglevel-serverSend.js)

# Configuration
Add `loglevel` and `loglevel-serverSend` scripts to your page first. Then configure the plugin:

##loglevelServerSend(logger, options)
Extend loglevel with new plugin which will send log information to the log-sever

| Param | Type | Description |
| ----- | ---- | ----------- |
| logger | <code>object</code> | loglevel instance to be extended |
| options | <code>object</code> |  |
| \[options.url=<code>&#x27;http://localhost:8000/main/log&#x27;</code>\] | <code>string</code> | Server url which would be used as a log server |
| \[options.prefix=<code>null</code>\] | <code>string</code> \| <code>function</code> | Prefix for all log messages. Either string or function wich should return string and accept log severity and message as parameters |
| \[options.callOriginal=<code>false</code>\] | <code>Bool</code> | If set to true - original loglevel method for logging would be called |

**Example**  
```js
loglevelServerSend(log,{url:'https://example.com/app/log',prefix: function(logSev,message) {
    return '[' + new Date().toISOString() + '] ' + logSev + ': ' + message + '\n'   
}})
```

# Servers
It should be fairly easy to create a server which will store all the log messages, but most probably [node-log-server](https://github.com/divhide/node-log-server) would be good enough for you
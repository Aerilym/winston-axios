# Winston-Axios

An axios transport for winston which allows for sending REST requests to an external API.

## Usage

### Create a logger with an Axios Transport

```JavaScript
const winston = require('winston');
const { AxiosTransport } = require('winston-axios');

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.json(),
  transports: [
    new AxiosTransport({
      host: 'http://localhost:9999/',
      path: 'log',
      auth: 'abc123',
    }),
  ],
});
```

### Add an Axios Transport to an existing logger

```JavaScript
const { AxiosTransport } = require('winston-axios');

logger.add(
  new AxiosTransport({
    host: 'http://localhost:9999/',
    path: 'log',
    auth: 'abc123',
  })
);
```

## Documentation

<dl>
<dt><a href="#AxiosTransportOptions">AxiosTransportOptions</a></dt>
<dd><p>Options for Axios Transport.</p>
</dd>
<dt><a href="#AxiosTransport">AxiosTransport</a></dt>
<dd><p>Transport for Winston that sends log messages to a remote server using Axios.</p>
</dd>
</dl>

<a name="AxiosTransportOptions"></a>

## AxiosTransportOptions

Options for Axios Transport.

| Param    | Type                             | Description                                                                                         |
| -------- | -------------------------------- | --------------------------------------------------------------------------------------------------- |
| url      | <code>string</code>              | The url to send the logs to.                                                                        |
| path     | <code>string</code>              | The path to send the logs to. The destination url will resolve to url + path.                       |
| auth     | <code>string</code>              | The authentication token to send with the logs. Will override any auth headers provided in headers. |
| authType | <code>TransportAuthType</code>   | The type of authentication to use.                                                                  |
| method   | <code>TransportMethod</code>     | The method to use when sending the logs.                                                            |
| headers  | <code>AxiosRequestHeaders</code> | The headers to send with the logs.                                                                  |

<a name="AxiosTransport"></a>

## AxiosTransport

Transport for Winston that sends log messages to a remote server using Axios.

**See**: [AxiosTransportOptions](#AxiosTransportOptions)  
<a name="new_AxiosTransport_new"></a>

### new AxiosTransport(options)

| Param   | Type                                                         | Description                    |
| ------- | ------------------------------------------------------------ | ------------------------------ |
| options | [<code>AxiosTransportOptions</code>](#AxiosTransportOptions) | The options for the transport. |

**Example**

```js
const logger = createLogger({
  transports: [
    new AxiosTransport({
      url: 'http://localhost:3000',
      path: '/logs',
    }),
  ],
});
logger.log({ level: 'info', message: 'Hello World' });
```

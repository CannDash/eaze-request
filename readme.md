# eaze-request [![Build Status](https://travis-ci.org/eaze/eaze-request.svg?branch=master)](https://travis-ci.org/eaze/eaze-request)

> Make requests to the Eaze API


## Install

```
$ npm install --save eaze-request
```


## Usage

```js
var Eaze = require('eaze-request')

var request = Eaze({baseUrl: 'https://the/api/base'})
request('the/endpoint', options, function (err, data) {
  //=> err = null / Error
  //=> data = {...} / undefined
})
```

## API

#### `Eaze(options)` -> `function`

Returns the `request` function.

##### options

Type: `object`
Default: `{baseUrl: '', method: 'get', json: true, timeout: 15000}`

Default options to be used with all requests made by the client.


#### `request(path, [options], [callback])` -> `request`

##### path

*Required*  
Type: `string`

The API request path.

##### options

Request settings, mostly passed to [xhr-request](https://github.com/Jam3/xhr-request).

Type: `object`  
Default: `{}`

###### token

Type: `string`

A token to use as the `X-Auth-Token` header.

##### callback

Type: `function`  
Arguments: `err, data`

###### err

Type: `error`

A request error. Responses with non-200 range status codes are considered errors. If the server sent an error message, that message will be used. If not, a generic HTTP message will be provided instead. Errors will always have a `statusCode` property.

###### data

Type: `object`

The JSON response data.

#### `request.onResult(listener)` -> `function`

Listens on all responses. Returns an unlisten function.

##### listener

Type: `function`  
Arguments: `data`

`data` contains:
* `method`
* `path`
* `query`
* `status`
* `timeout`
* `times` (`{start, end}`)
* `duration`

## License

MIT © [Ben Drucker](http://bendrucker.me)

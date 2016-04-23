
# Forum

Inter connection library with auto discovery on local network

## Todo

- [ ] Add module to detect free, internet opened port instead of listening on 0 (random port)
- [ ] Allow to specify IPs to connect to
- [ ] Allow to pass certificates to connection

# airswarm fork

Network swarm that automagically discovers other peers on the network using multicast dns

```
npm install airswarm
```

[![build status](http://img.shields.io/travis/mafintosh/airswarm.svg?style=flat)](http://travis-ci.org/mafintosh/airswarm)

## Usage

``` js
var airswarm = require('airswarm')

airswarm('testing', function (sock) {
  sock.write('hello world (' + process.pid + ')\n')
  sock.pipe(process.stdout)
})
```

If you run the above program in a couple of processes on the same local network
the swarms should start connecting to each other and write hello world

## API

#### `swarm = airswarm(name, [options], [onpeer])`

Create a new swarm. The `swarm` will emit `peer` everytime a new peer
is connected. Optionally you can pass a `peer` listener as the second argument.

The `peer` will be a tcp stream to another swarm.

Options include

``` js
{
  limit: maxPeersToConnectTo // defaults to Infinity
}
```

#### `swarm.peers`

An array containing all the currently connected peers

## License

MIT

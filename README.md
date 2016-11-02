# hypername

Distributed name server

```
npm install -g hypername
```

## Usage

On one computer

``` sh
hypername init some.db
<prints-key>
```

On another

``` sh
hypername init some-other.db <key-printed-above>
```

Now the first computer will be able to share name=value pairs with the other one

On the first computer do

``` sh
hypername set some.db hello world
hypername sync some.db
```

On the other

``` sh
hypername sync some-other.db --exit # exit after first change
hypername get some-other.db hello # prints world
```

## API
```txt
  Usage:
    $ hypername <command> [options]

  Commands:
    init <path>              Initialize a hypername database in a path
    set <db> <key> <value>   Save a value in the store
    get <db> <key>           Get a value from the store
    list <db>                List all key value-pairs
    sync <db>                Connect to the swarm and synchronize data

    Options:
      -h, --help              Print usage
          --exit              Exit after the first download

  Examples:
    $ hypername init ./name.db         # start hypername & print key
    $ hypername set ./name.db hi cat   # save a key-value pair
    $ hypername get ./name.db hi       # get a value at a key
    $ hypername list ./name.db         # list all key-value pairs
    $ hypername sync ./name.db         # sync hypername over the network
```

## License

MIT

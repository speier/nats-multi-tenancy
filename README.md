# Multi tenancy with NATS

Small proof of concept to try out nats multi tenancy features (accounts, imports/exports and leafnodes).

## Usage

Services are running in docker, to spin up the cluster simply run:

```sh
❯ docker-compose up # use `-d` to run in the background
```

Try leafnodes:

```sh
# subscribe to leafnode `a` and `b` (note the different port numbers)
❯ nats -s a:@localhost:4223 sub foo
❯ nats -s b:@localhost:4224 sub foo

# publish on main as user `a` and user `b`
❯ nats -s a:@localhost:4222 pub foo bar
❯ nats -s b:@localhost:4222 pub foo bar
```

Try imports/exports:

```sh
# subscribe to leafnode `a`
❯ nats -s a:@localhost:4223 sub foo.bar

# publish on main as user `sys`
❯ nats -s sys:@localhost:4222 pub foo.bar 1
```

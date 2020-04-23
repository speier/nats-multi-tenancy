# nats with leafnodes

Just a small proof of concept to test nats with leafnodes.

## usage

Services are running in docker, to spin up the cluster simply run:

```sh
❯ docker-compose up # use `-d` to run in the background
```

Testing the topology to see it works as expected:

```sh
# subscribe to leafnode `a` and `b` (note the different port numbers)
❯ nats -s a:@localhost:4223 sub foo
❯ nats -s b:@localhost:4224 sub foo

# publish on main as user `a` and user `b`
❯ nats -s a:@localhost:4222 pub foo bar
❯ nats -s b:@localhost:4222 pub foo bar
```

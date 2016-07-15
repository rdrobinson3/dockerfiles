# distcc-alpine

Lightweight alpine-based distcc server with gcc and g++ included.

## Usage

### Start the distcc daemon

```
docker run -it --rm -p 3632:3632 thedrhax/distcc-alpine:latest
```

### Configure the distcc client

```
apt-get install distcc
export DISTCC_HOSTS="localhost/threads container_address/threads" # replace 'threads' with the number of CPUs on this node
export PATH="/usr/lib/distcc/bin:/usr/lib/distcc:$PATH" # path to distcc's binaries changes between distributions
```

### Distribute the compilation process

```
make ...
```

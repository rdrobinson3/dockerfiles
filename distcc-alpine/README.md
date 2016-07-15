# Distcc

Lightweight alpine-based distcc server.

## Included tools

* distcc daemon
* gcc (cc)
* g++ (cpp)

## Example

* Start distcc daemon
```
docker run -it --rm -p 3632:3632 thedrhax/distcc-alpine:latest
```

* Use distcc client to distribute the compilation process
```
apt-get install distcc

export DISTCC_HOSTS="localhost/threads container_address/threads" # replace 'threads' with the number of CPUs on this node
export PATH="/usr/lib/distcc/bin:/usr/lib/distcc:$PATH" # path to distcc's binaries changes between distributions

make ...
```

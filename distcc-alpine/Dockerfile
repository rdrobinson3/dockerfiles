FROM alpine:latest

MAINTAINER Dmitry Karikh <the.dr.hax@gmail.com>

# Install distcc, gcc, g++
RUN apk --no-cache add distcc gcc g++

EXPOSE 3632

ENTRYPOINT ["/usr/bin/distccd"]

CMD ["--no-detach", "--log-stderr", "--verbose", "-a", "0.0.0.0/0"]

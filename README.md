
Install: `go get github.com/grahamking/latency`

Run: `sudo latency [hostname]`.

Example output:

> $ sudo bin/latency github.com
> Measuring round-trip latency from 192.168.1.26 to 192.30.252.131 on port 80
> Latency: 116.601914ms

The `sudo` is needed to open a raw socket.

`latency` sends a TCP SYN packet (the opening of the three-way handshake) to a remote host on port 80. That host will respond with either a RST (if the port is closed), or a SYN/ACK (if the port is open). Either way, we time how long it takes between sending the SYN and receiving the response. That's your network latency.

There are of course many other ways to measure this ([mtr](https://en.wikipedia.org/wiki/MTR_%28Software%29) is nice), but this is a fun exercise in using raw sockets and binary encoding in Go.

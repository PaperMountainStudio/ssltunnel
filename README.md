# ssltunnel

Do you want to feel **uncomfortably secure**, but don't want to set up a real SSL enabled web server for your development environment?

*Good News!* `ssltunnel` is the answer!

## Installation

If you don't have [Go][] on your system, I have some [precompiled binaries available][releases]. I don't have access to test all of them though so if there is a problem please let me know.

If you have Go installed on your system:

```bash
$ go get github.com/jakebasile/ssltunnel
```

## Usage

```bash
$ ssltunnel -wrap 8080 -serve 8443
```

This will start listening on `0.0.0.0:8443` with SSL, proxying all requests to `127.0.0.1:8080`. It automatically makes a self signed cert covering the ip address `0.0.0.0`. If you want to use a special hostname, do this instead:

```bash
$ ssltunnel -in 8080 -out 8443 -hosts superspecial.example.com,superspecial2.example.com
```

Then, you can either modify your `/etc/hosts` file to point those host names to `127.0.0.1` or set up your own DNS magic.

*NOTE*: If you want to change the hostname you need to delete the key and cert file already generated.

[releases]: https://github.com/jakebasile/ssltunnel/releases
[Go]: http://golang.org/


# aprsc - an APRS-IS server in C

You're looking at the source code of aprsc, an open-source APRS-IS
server. This Code was initially written by [Hessu, OH7LZB](https://github.com/hessu/aprsc). Upstream server connections in his work are not filterable. You always got the full APRS-IS stream (abt 19k/s).

Additionally some code was added by [dgentges](https://github.com/dgentges) which made the upstream server-connection filterable.

So if you plan to run an "APRS-IS server" within your own network (and there are plenty of reasons to do so) then THIS is the repo to start.

## Installation

```shell
cd ~
git clone https://github.com/ploeffler/aprsc
cd aprsc/src
./configure
make
sudo make install
```

This will install the entire server in /opt/aprsc. The config-file is in etc/.

## Configuration

The magic trick is the following line:

```shell
Uplink "Core filtered" full  tcp  rotate.aprs.net 14580 filter r/46.0/15.0/1000
```

If you are not familiar with the use of server-side filters: please [check this page](https://www.aprs-is.net/javAPRSFilter.aspx)

## Docker

A dockerized version of this server is available at [this repo](https://github.com/ploeffler/aprsc-docker)

## Additional information

For more information, please refer to the following resources:

* [Home page](http://he.fi/aprsc/)
* [Installation instructions](http://he.fi/aprsc/INSTALLING.html)
* [Source code downloads](http://he.fi/aprsc/down/)
* [Conference paper, Digital Communications Conference 2012, Atlanta, GA](http://he.fi/aprsc/dcc-2012-aprsc.pdf)
* [Contributing to the aprsc project](http://he.fi/aprsc/CONTRIBUTING.html)

Have fun!

Peter, OE6PLD 

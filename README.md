
# aprsc - an APRS-IS server in C

You're looking at the source code of aprsc, an open-source APRS-IS
server. This Code was initially written by [Hessu, OH7LZB](https://github.com/hessu/aprsc). Upstream server connections in his work are not filterable. You always got the full APRS-IS stream (abt 19k/s).

Additionally some code was added by [dgentges](https://github.com/dgentges) that made the upstream server-connection filterable.

## Reasons to run APRSc on your local network

Maybe you have a direwolf setup running your 2m and/or 70cm APSR station. Ofcourse dirwolf needs a connection to the APRS-IS network to send/receive data from.
Other devices, be it your LoRa-Gateway , the weather-station, the baloon-tracker, ... also require a connection to these servers. The same applies for your prefered user-program (xastir, UiView, ..)

So at the end you have a dedicated server-connection for any of these. Every connection produces (it may be very little) load on the APRS-IS core server that is connected to. In addition, if your internet (or 44.0.0.0/8) connection is lost, you are relatively blind.

Here comes a locally running instance of an "APRS-IS" server into play. The packages, that are included in some linux distros, request the full feed of the upstream server, that generate a constant datastream of about 19kB/s, which can exhaust your datavolume at some time. The additions of [dgentges](https://github.com/dgentges) to the original APRSc code implement the ability to filter the upstream (to be precise, its the downstream) server connection with the well known serverside filter commands.

Running your own, local APRSc has the following advantages:

- never be blind when internet is down
- reduce the load on the core servers
- reduce the bandwith needed for APRS-data

## Installation

```shell
cd ~
apt-get install build-essential autoconf make git vim libevent-dev -y
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


Have fun!

Peter, OE6PLD 

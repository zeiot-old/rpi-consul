# RPI Consul

* Master : [![coverage report](https://gitlab.com/zeiot/rpi-consul/badges/master/coverage.svg)](https://gitlab.com/zeiot/rpi-consul/commits/master)

Docker image of [Consul][] to use on a [Raspberry PI][].

Configure binfmt-support on the Docker host (works locally or remotely, i.e: using boot2docker):

    $ docker run --rm --privileged multiarch/qemu-user-static:register --reset

Then you can run an armhf image from your x86_64 Docker host :

    $ make run version=x.x

Or build :

    $ make build version=x.x


# Supported tags

* [![](https://images.microbadger.com/badges/version/zeiot/rpi-consul:0.8.3.svg)](https://microbadger.com/images/zeiot/rpi-consul:0.8.3 "Get your own version badge on microbadger.com")


## License

See [LICENSE](LICENSE) for the complete license.


## Changelog

A [ChangeLog.md](ChangeLog.md) is available.


## Contact

Nicolas Lamirault <nicolas.lamirault@gmail.com>


[Raspberry PI]: https://www.raspberrypi.org/
[Consul]: https://www.consul.io/

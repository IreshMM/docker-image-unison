## Usage
The tags are structured as `docker.io/ireshmm/unison:$UNISON_VERSION-$OCAML_VERSION-$ARCH` so for example

```
# this will pull the AMD or ARM version, depending on your current arch
docker pull ghcr.io/eugenmayer/unison:2.52.1-4.12.0
```

### What does it do ?

This image simply runs an unison server on the internal port `5000` with the specified user/uid. If the user/uid doesn't
exist, it is created/modified on startup.

## Building

You can build your own image using

`docker build --build-arg "OCAML_VERSION=<ocaml-version>" --build-arg "UNISON_VERSION=<unison-version>" -t custom-docker-image-unison .`

where `ocaml-version` is any OCaml version available as source-code [here](http://caml.inria.fr/pub/distrib/) and `unison-version` is any Unison version available as source code [here](https://github.com/bcpierce00/unison/releases/).

Or for arm base builds change the image using BASE_IMAGE

`docker build --build-arg "BASE_IMAGE=arm64v8/alpine:3.12" --build-arg "OCAML_VERSION=<ocaml-version>" --build-arg "UNISON_VERSION=<unison-version>" -t custom-docker-image-unison .`

### Build Examples

For example,

`docker build --build-arg "OCAML_VERSION=4.12.0" --build-arg "UNISON_VERSION=2.52.1" -t custom-docker-image-unison .`

The configuration in the docker-sync.yml would then be:

_unison_image_: 'custom-docker-image-unison'

A lot of credits go to [mickaelperrin](https://github.com/mickaelperrin) - most of the work has been done by him initially.


## Credits

- Big thanks at [mickaelperrin](https://github.com/mickaelperrin) for putting hard work into getting this production ready.

## License

What the others did, so:
This docker image is licensed under GPLv3 because Unison is licensed under GPLv3 and is included in the image. See LICENSE.

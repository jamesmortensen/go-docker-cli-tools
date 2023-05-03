# get-image-sha256-digest

This is a simple CLI tool to get the sha256 digest for container images hosted on Docker Hub. The sha256 hashes uniquely identify container images. The hashes are helpful when browsing container image tags on Docker Hub in order to determine if the tag refers to the same images. In the case of multi-arch images, there will be more than one sha256 digest.

## Usage

Using the Docker Hub v2 API, replace the ORGANIZATION, IMAGE, and TAG path variables with the values from the image name and tag.

Container image format:
- hostname/image_name:tag

```
$ go run get-image-sha256-digest.go https://hub.docker.com/v2/repositories/$HOSTNAME/$IMAGE_NAME/tags/$TAG
```


## Example

If the container image you wish to retrieve digests for is `seleniarm/standalone-chromium`, then use the following command to retrieve them:

```
$ go run get-image-sha256-digest.go https://hub.docker.com/v2/repositories/seleniarm/standalone-chromium/tags/latest/
arm64 sha256:2c038c6717f4d93490416f8006d9533f3ffdb5b77ac86c7f7b1c1659a42ca755
amd64 sha256:8220a7a9bc920e0a5da3f13e42eaa88030a91c4810ccb21181145edec350a679
arm sha256:f8f16f454bef3d7b093b2113f935d8244a5d97f75e8550aab464d40e9e2baa5b
```

These sha265 digests match what's on the Docker Hub website for that container image repository:

| DIGEST | OS/ARCH | COMPRESSED SIZE |
| ------ | ------- | --------------- |
| 8220a7a9bc92 | linux/amd64  | 615.42 MB |
| f8f16f454bef | linux/arm/v7 | 546.91 MB |
| 2c038c6717f4 | linux/arm64  | 582.24 MB |


## License

Copyright (c) James Mortensen, 2022 MIT License

# gomobile Android builds... in Docker!

You can build native and SDK Android applications in Go, as described on [the wiki](https://github.com/golang/go/wiki/Mobile). That requires the Android SDK and NDK are installed and set up, at least for building SDK applications (.aar). This docker container installs all the required Android dependencies, as well as `gomobile`. This makes for much easier Android builds across multiple platforms and machines. It also allows for easy CI builds, like on GitHub Actions.

## Versions
- Go version: 1.17.8
- gomobile commit: 447654d
- Android platform version: 31

You can change these easily in the [Dockerfile](Dockerfile) and build your own container image. In the future, maybe multiple tags will be published to allow for different options.

## Usage

*Note: the image is 4.1 GB*

Enter the directory of your Go project, and then run:

```
docker run --rm -v "$PWD":/module makeworld/gomobile-android ...
```

Replace `...` with whatever arguments you'd provide to `gomobile` normally. For example:

```
docker run --rm -v "$PWD":/module makeworld/gomobile-android bind -target=android/arm -o test.aar .
```

`"$PWD"` means your current working directory, so `-v "$PWD":/module` mounts your working directory to `/module` in the docker container. If you want to specify the path to your Go project manually, you can do `-v /path/to/dir:/module` instead.


## License

This repo is dual-licensed under the MIT and APACHE2 licenses. Please see [LICENSE-MIT](LICENSE-MIT) and [LICENSE-APACHE2](LICENSE-APACHE2) for details.

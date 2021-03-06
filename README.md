# VLC MEDIA PLAYER ON DOCKER

Dockerizing the awesome [VLC Media Player](https://www.videolan.org/).


## How to Install

All we need is to download this package and add the bash script `bin/vlc.sh` to our path.

Lets assume that your path is in `/usr/bin` and that this package will be located in `~/.vlc`.

Cloning the package...

```bash
git clone git@gitlab.com:exadra37-docker/media-player/vlc.git ~/.vlc
```

Creating the sym link...

```bash
sudo ln -s ~/.vlc/bin/vlc.sh /usr/bin/vlc
```

Building the Docker Image...

```bash
sudo docker build -t exadra37/vlc ~/.vlc/docker/build
```

## How to use

No matter how we start `vlc` it will map always the current folder into inside the Docker Container
at `/home/vlc/media`.

### To open only the Graphical User Interface

```bash
vlc
```

### To open from a url

I love Elixir programing language, thus here it goes a link to one of my favorite videos about why
Developers should be using it...

```bash
vlc https://www.youtube.com/watch?v=pO4_Wlq8JeI
```

### To open a file

```bash
vlc path/to/file.extension
```

### To open a file with compressed folders

```bash
vlc path/to/file/with/compressed/folders.zip
```

### To open a folder

```bash
vlc path/to/folder
```

## VLC Shared Folders Between Host and Docker Container

In order to have our media available inside the docker container we need to map it from the host.

Also to persist data from VLC running inside a docker container we need to map some folders 
between the host and the container.

### Mapped Folders

* Media - `$PWD` into `/home/vlc/media`.
* Configuration - `~/.docker-vlc/.config` into `/home/vlc/.config`.
* Cache - `~/.docker-vlc/.cache` into `/home/vlc/.cache`.
* Snapshots - `~/Pictures/VLC/Snapshots` into `/home/vlc/snapshots`.

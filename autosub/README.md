Auto generate subtitles with [ffmpeg](https://ffmpeg.org/) + [autosub](https://github.com/agermanidis/autosub)

Usage:

```bash
# build image
docker-compose build

# help
docker run --rm -it weshigbee/autosub 

# run, mounting working dir into container working dir
# this generates my.srt with subtitles 
docker run --rm -it -v ${PWD}:/host -w /host weshigbee/autosub my.mp4
```

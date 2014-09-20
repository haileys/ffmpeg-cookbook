## ffmpeg-cookbook

ffmpeg is a super powerful tool but its 'user interface' is arcane at best.
Every time I need to use it, I end up spending half an hour googling and
fudging around trying to get it to do what I want. To save myself (and
hopefully others) time in the future, I'm going to start collecting ffmpeg
examples in this repo. Feel free to send a pull request adding your own
examples if there's something useful I've missed.

All these examples are tested on this version of ffmpeg:

```
# ffmpeg -version
ffmpeg version 2.2
built on Mar 24 2014 08:40:58 with gcc 4.8.2 (GCC) 20140206 (prerelease)
configuration: --prefix=/usr --disable-debug --disable-static --enable-avresample --enable-dxva2 --enable-fontconfig --enable-gnutls --enable-gpl --enable-libass --enable-libbluray --enable-libfreetype --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libv4l2 --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-libxvid --enable-pic --enable-postproc --enable-runtime-cpudetect --enable-shared --enable-swresample --enable-vdpau --enable-version3 --enable-x11grab
libavutil      52. 66.100 / 52. 66.100
libavcodec     55. 52.102 / 55. 52.102
libavformat    55. 33.100 / 55. 33.100
libavdevice    55. 10.100 / 55. 10.100
libavfilter     4.  2.100 /  4.  2.100
libavresample   1.  2.  0 /  1.  2.  0
libswscale      2.  5.102 /  2.  5.102
libswresample   0. 18.100 /  0. 18.100
libpostproc    52.  3.100 / 52.  3.100
```

### Transcoding a .mov to an .mp4

Converts a .mov video file into a .mp4 video file

```
ffmpeg -i input.mov -strict -2 output.mp4
```

If it's a vertical video from an iPhone (shame!) then you'll need to tell
ffmpeg to rotate it when writing the output file:

```
ffmpeg -i input.mov -vf transpose=1 -strict -2 output.mp4
```

### Extracting audio from a video

Extracts a wave file from the input video file.

```
ffmpeg -i input.mov -acodec pcm_s16le -ac 2 output.wav
```

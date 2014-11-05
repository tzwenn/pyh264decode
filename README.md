PyH264Decode
============


This is a small Python module to decode raw H.264 packets with external avcC extra data ([ISO/IEC 14496:15](http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=55980)).

It wraps ffmpeg's libavcodec and returns YUV420p frames, with the lineskip being the actual width of each frame.

## Installing

This module is currently only tested with Python 2.7.
You'll need ffmpeg (tested with 2.4.2) or libav with H.264 support installed.

```bash
$ python setup.py build
$ sudo python setup.py install
$ pydoc h264decode
```

## Usage

```python
import h264decode

decoder = h264decode.Decoder(avccPacket)
for frame in frameGenerator:
	yuv = decoder.decodeFrame(frame)
	print "Read frame of %dx%d pixels" % (yuv.width, yuv.height)
	# e.g. rendering with pygame:
	overlay.display((yuv.y, yuv.u, yuv.v))
```

## License
Code is under the [BSD 2 Clause (NetBSD) license](https://github.com/tzwenn/pyh264decode/tree/master/LICENSE.txt).

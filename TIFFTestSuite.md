# Introduction #

The TIFF testsuite is a collection of [TIFF images](http://en.wikipedia.org/wiki/Tagged_Image_File_Format) from publicly available sources, intended to help verify the correct operation of TIFF image decoders when presented with malformed or esoteric characteristics.

It is not the intention of this testsuite to verify the correct rendering of images, but rather to ensure safe operation when presented with malformed data, esoteric characteristics, edge cases, and pathological input.

Your decoder or application should gracefully handle any errors while attempting to render these images. To read more about how these testsuites are generated and their intended use, see AboutTestSuite.

# Specification #

These images were selected based on the number of execution paths explored with [tiff-4.0.0beta3](http://www.libtiff.org).

Approximately 8797 unique lines of code are executed when decoding the testsuite using tiff-4.0.0beta3.

## Coverage ##

![http://chart.apis.google.com/chart?chs=500x250&chd=t:0,0,38,47,0,67,661,194,2343,0,29,11,12,901,0,654,296,353,0,1439,159,60,0,224,437,191,132,59,105,148,100,0,11,0,126&chl=stat.h|sysmacros.h|tif_aux.c|tif_close.c|tif_codec.c|tif_compress.c|tif_dir.c|tif_dirinfo.c|tif_dirread.c|tif_dirwrite.c|tif_dumpmode.c|tif_error.c|tif_extension.c|tif_fax3.c|tif_flush.c|tif_jpeg.c|tif_luv.c|tif_lzw.c|tif_next.c|tif_ojpeg.c|tif_open.c|tif_packbits.c|tif_pixarlog.c|tif_predict.c|tif_print.c|tif_read.c|tif_strip.c|tif_swab.c|tif_thunder.c|tif_tile.c|tif_unix.c|tif_version.c|tif_warning.c|tif_write.c|tif_zip.c&cht=p&chtt=Distribution%20of%20Executed%20Lines%20by%20File&ft=.png](http://chart.apis.google.com/chart?chs=500x250&chd=t:0,0,38,47,0,67,661,194,2343,0,29,11,12,901,0,654,296,353,0,1439,159,60,0,224,437,191,132,59,105,148,100,0,11,0,126&chl=stat.h|sysmacros.h|tif_aux.c|tif_close.c|tif_codec.c|tif_compress.c|tif_dir.c|tif_dirinfo.c|tif_dirread.c|tif_dirwrite.c|tif_dumpmode.c|tif_error.c|tif_extension.c|tif_fax3.c|tif_flush.c|tif_jpeg.c|tif_luv.c|tif_lzw.c|tif_next.c|tif_ojpeg.c|tif_open.c|tif_packbits.c|tif_pixarlog.c|tif_predict.c|tif_print.c|tif_read.c|tif_strip.c|tif_swab.c|tif_thunder.c|tif_tile.c|tif_unix.c|tif_version.c|tif_warning.c|tif_write.c|tif_zip.c&cht=p&chtt=Distribution%20of%20Executed%20Lines%20by%20File&ft=.png)
![http://chart.apis.google.com/chart?chs=500x250&chd=t:12,9,184,19,34,110,592,282,2122,2095,33,25,47,838,58,762,1074,358,82,601,219,164,1340,381,129,360,110,69,5,80,27,3,25,535,148&chl=stat.h|sysmacros.h|tif_aux.c|tif_close.c|tif_codec.c|tif_compress.c|tif_dir.c|tif_dirinfo.c|tif_dirread.c|tif_dirwrite.c|tif_dumpmode.c|tif_error.c|tif_extension.c|tif_fax3.c|tif_flush.c|tif_jpeg.c|tif_luv.c|tif_lzw.c|tif_next.c|tif_ojpeg.c|tif_open.c|tif_packbits.c|tif_pixarlog.c|tif_predict.c|tif_print.c|tif_read.c|tif_strip.c|tif_swab.c|tif_thunder.c|tif_tile.c|tif_unix.c|tif_version.c|tif_warning.c|tif_write.c|tif_zip.c&cht=p&chtt=Distribution%20of%20Unexecuted%20Lines%20by%20File&ft=.png](http://chart.apis.google.com/chart?chs=500x250&chd=t:12,9,184,19,34,110,592,282,2122,2095,33,25,47,838,58,762,1074,358,82,601,219,164,1340,381,129,360,110,69,5,80,27,3,25,535,148&chl=stat.h|sysmacros.h|tif_aux.c|tif_close.c|tif_codec.c|tif_compress.c|tif_dir.c|tif_dirinfo.c|tif_dirread.c|tif_dirwrite.c|tif_dumpmode.c|tif_error.c|tif_extension.c|tif_fax3.c|tif_flush.c|tif_jpeg.c|tif_luv.c|tif_lzw.c|tif_next.c|tif_ojpeg.c|tif_open.c|tif_packbits.c|tif_pixarlog.c|tif_predict.c|tif_print.c|tif_read.c|tif_strip.c|tif_swab.c|tif_thunder.c|tif_tile.c|tif_unix.c|tif_version.c|tif_warning.c|tif_write.c|tif_zip.c&cht=p&chtt=Distribution%20of%20Unexecuted%20Lines%20by%20File&ft=.png)

### Coverage Gaps ###

The majority of the unexecuted code is from the writing routines, whice are largely unused during decoder testing. A large portion of the code also handles runtime allocation failure.

# Testsuite Contents #
## Legend ##

| **Tag** | **Description**  |
|:--------|:-----------------|
| **T**   | **Trivial**<br>Any artistic/creative content contained in the image is believed to be ineligible for copyright, as it's trivial (solid colour, single pixel, simple shapes or patterns, etc.) (please note, <a href='http://en.wikipedia.org/wiki/IANAL'>IANAL</a>). See also, TrivialContent. <br>
<tr><td> <b>F</b>   </td><td> <b>Free</b><br>The image is believed to be compatible with common free software distribution guidelines, such as <a href='http://en.wikipedia.org/wiki/Public_domain'>PD</a>, <a href='http://en.wikipedia.org/wiki/Creative_Commons'>CC</a>, or <a href='http://en.wikipedia.org/wiki/GFDL'>GFDL</a>. See also, ImageFreedom.</td></tr>
<tr><td> <b>O</b>   </td><td> <b>Origin Unkown</b><br>The original creator or source of the image is currently unknown. Please <a href='http://code.google.com/p/imagetestsuite/issues/'>create a new issue</a> if you know the origin or creator, or can provide a replacement image. See also, OriginUnknown. </td></tr>
<tr><td> <b>N</b>   </td><td> <b>NSFW (Not Safe For Work)</b><br>The image may contain potentially objectionable content. Please <a href='http://code.google.com/p/imagetestsuite/issues/'>create a new issue</a> if you have a suitable replacement image. See also, ObjectionableContent. </td></tr>
<tr><td> <b>U</b>   </td><td> <b>Fair Use / Fair Dealing</b><br>The original source image is known to be distributed under a restrictive license, however, it is believed that it's use in verifying the correct operation of image decoders is <a href='http://en.wikipedia.org/wiki/Fair_use'>fair use</a>/<a href='http://en.wikipedia.org/wiki/Fair_dealing'>fair dealing</a> (non-commercial research) (please note, <a href='http://en.wikipedia.org/wiki/IANAL'>IANAL</a>). Please <a href='http://code.google.com/p/imagetestsuite/issues/'>create a new issue</a> if you have a suitable replacement image. See also, CopyrightIssues. </td></tr></tbody></table>

<h2>Naming Convention</h2>

Images are named based on the md5 checksum of the original source image, prefixed<br>
with modifier letters, for example<br>
<br>
<pre><code>c-m8-d41d8cd98f00b204e9800998ecf8427e.tif<br>
</code></pre>

This is an 8th generation mutation of a source image with checksum<br>
d41d8cd98f00b204e9800998ecf8427e, and at least one error has been<br>
corrected.<br>
<br>
<h2>Images</h2>

<h3>023c970a2a16794f9e51101f76d3bf4d.tif</h3>

<ul><li>Origin: <code>http://www.weatherchannel.com.au/tippingmedia/3.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x2e9e6 (190950)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 689 Image Length: 217<br>
  Resolution: 96, 96 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  YCbCr Positioning: 0 (0x0)<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 217<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-1<br>
  White Point: 0-0<br>
  PrimaryChromaticities: 0.000000,0.000000,0.000000,0.000000,0.000000,0.000000<br>
  YCbCrCoefficients: 0.000000,0.000000,0.000000<br>
  Reference Black/White:<br>
     0:     0     0<br>
     1:     0     0<br>
     2:     0     0<br>
  EXIFIFDOffset: 0x108<br>
  Predictor: horizontal differencing 2 (0x2)<br>
<br>
</code></pre>
<h3>034ed0549f9046b9c370ac26550a60da.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x18 (24)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 664 Image Length: 813<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: None<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: halftone or dithered scan<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 813<br>
  Planar Configuration: single image plane<br>
<br>
</code></pre>
<h3>0c84d07e1b22b76f24cccc70d8788e4a.tif</h3>

<ul><li>Origin: <code>http://downloads.bistum-augsburg.de/6/562/1/70846786833481925294.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x440ec (278764)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 246 Image Length: 345<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 345<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop CS2 Windows<br>
  DateTime: 2008:03:09 23:30:21<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 8550 bytes<br>
  EXIFIFDOffset: 0x441f0<br>
TIFF Directory at offset 0x47116 (291094)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1748 Image Length: 2480<br>
  Resolution: 300, 300 pixels/inch<br>
  Position: 0, 0<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 293<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 294106<br>
  Model: CanoScan N650U/N656U<br>
  Software: Microsoft Office Document Scanning  1.03.2349.01 <br>
  DateTime: 2008:03:09 13:07:32<br>
  Artist: Rosa<br>
TIFF Directory at offset 0x4b504 (308484)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1748 Image Length: 2480<br>
  Resolution: 300, 300 pixels/inch<br>
  Position: 0, 0<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 293<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 311882<br>
  Model: CanoScan N650U/N656U<br>
  Software: Microsoft Office Document Scanning  1.03.2349.01 <br>
  DateTime: 2008:03:09 13:08:27<br>
  Artist: Rosa<br>
TIFF Directory at offset 0x4f6a4 (325284)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1748 Image Length: 2480<br>
  Resolution: 300, 300 pixels/inch<br>
  Position: 0, 0<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 293<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 328042<br>
  Model: CanoScan N650U/N656U<br>
  Software: Microsoft Office Document Scanning  1.03.2349.01 <br>
  DateTime: 2008:03:09 13:09:07<br>
  Artist: Rosa<br>
<br>
</code></pre>
<h3>0ceffbda821c7564352b313bed43f7c7.tif</h3>

<ul><li>Origin: <code>http://wko.at/wknoe/rp/gdb/bacopa.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x108bc (67772)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1728 Image Length: 2206<br>
  Resolution: 204, 196 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 146<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.00P, (c) Wang Labs, Inc. 1990, 1991<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2230<br>
  Resolution: 204, 196<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: msb-to-lsb<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-3<br>
  Software: Topcall TIFF Writer V.: 2.12.08 / Mar  2 2000<br>
TIFF Directory at offset 0x7f0c (32524)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2292<br>
  Resolution: 204, 196<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: msb-to-lsb<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-3<br>
  Software: Topcall TIFF Writer V.: 2.12.08 / Mar  2 2000<br>
<br>
</code></pre>
<h3>m1-108af7a96a2efa82a0cee0f200e6b9a2.tif</h3>

<h3>m2-108af7a96a2efa82a0cee0f200e6b9a2.tif</h3>

<h3>m3-108af7a96a2efa82a0cee0f200e6b9a2.tif</h3>

<ul><li>Origin: <code>https://courses.washington.edu/art483/site/images/livingrobot-rear.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-108af7a96a2efa82a0cee0f200e6b9a2.tif:<br>
TIFF Directory at offset 0xbd0 (3024)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 800 Image Length: 3036676696<br>
  Resolution: 150, 150 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 600<br>
  Planar Configuration: single image plane<br>
  Make: NIKON<br>
  Model: E775<br>
  Software: E775v1.1u<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 88 bytes<br>
  ICC Profile: &lt;present&gt;, 1304 bytes<br>
  EXIFIFDOffset: 0xcde<br>
TIFF Directory at offset 0xcde (3294)<br>
  ExposureTime: 0.192308<br>
  FNumber: 2.800000<br>
  ExposureProgram: 2<br>
  ISOSpeedRatings: 100<br>
  ExifVersion: 0x30,0x32,0x31,0x30<br>
  DateTimeOriginal: 2006:11:23 14:46:39<br>
  DateTimeDigitized: 2006:11:23 14:46:39<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  CompressedBitsPerPixel: 3.000000<br>
  ExposureBiasValue: 0.000000<br>
  MaxApertureValue: 3.500000<br>
  MeteringMode: 5<br>
  LightSource: 0<br>
  Flash: 0<br>
  FocalLength: 5.800000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 1<br>
  PixelXDimension: 1600<br>
  PixelYDimension: 1200<br>
m2-108af7a96a2efa82a0cee0f200e6b9a2.tif:<br>
TIFF Directory at offset 0xbd0 (3024)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 800 Image Length: 600<br>
  Resolution: 150, 150 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 600<br>
  Planar Configuration: single image plane<br>
  Model: E775<br>
  Software: E775v1.1u<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 88 bytes<br>
  ICC Profile: &lt;present&gt;, 1304 bytes<br>
  EXIFIFDOffset: 0xcde<br>
TIFF Directory at offset 0xcde (3294)<br>
  ExposureTime: 0.192308<br>
  FNumber: 2.800000<br>
  ExposureProgram: 2<br>
  ISOSpeedRatings: 100<br>
  ExifVersion: 0x30,0x32,0x31,0x30<br>
  DateTimeOriginal: 2006:11:23 14:46:39<br>
  DateTimeDigitized: 2006:11:23 14:46:39<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  CompressedBitsPerPixel: 0.000000<br>
  ExposureBiasValue: 0.000000<br>
  MaxApertureValue: 3.500000<br>
  MeteringMode: 5<br>
  LightSource: 0<br>
  Flash: 0<br>
  FocalLength: 5.800000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 1<br>
  PixelXDimension: 1600<br>
  PixelYDimension: 1200<br>
m3-108af7a96a2efa82a0cee0f200e6b9a2.tif:<br>
TIFF Directory at offset 0xbd0 (3024)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 800 Image Length: 600<br>
  Resolution: 150, 150 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 600<br>
  Planar Configuration: single image plane<br>
  Model: E775<br>
  Software: E775v1.1u<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 88 bytes<br>
  ICC Profile: &lt;present&gt;, 1304 bytes<br>
  EXIFIFDOffset: 0xcde<br>
<br>
</code></pre>
<h3>m1-14847ce6f5fab0774dae9ad4fba31316.tif</h3>

<h3>m2-14847ce6f5fab0774dae9ad4fba31316.tif</h3>

<ul><li>Origin: <code>http://www.camarasertaozinho.sp.gov.br/images/010003535.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-14847ce6f5fab0774dae9ad4fba31316.tif:<br>
TIFF Directory at offset 0x130d2 (78034)<br>
  Image Width: 3296 Image Length: 4672<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 212<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  SMax Sample Value: 4672<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-0<br>
m2-14847ce6f5fab0774dae9ad4fba31316.tif:<br>
TIFF Directory at offset 0x130d2 (78034)<br>
  Image Width: 3296 Image Length: 4672<br>
  Resolution: 400, 0 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4672<br>
  SMax Sample Value: 78026<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-0<br>
<br>
</code></pre>
<h3>16f2a7e9adcda96170bc1fa873e275c1.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x11866 (71782)<br>
  Image Width: 333 Image Length: 225<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 16<br>
  Sample Format: signed integer<br>
  Compression Scheme: SGILog<br>
  Photometric Interpretation: CIE Log2(L)<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 8<br>
  Planar Configuration: single image plane<br>
  Sample to Nits conversion factor: 1.7900e+02<br>
<br>
</code></pre>
<h3>1af8e95246f4cfa4e5e58f67d6428ea3.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x1208 (4616)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 160 Image Length: 160<br>
  Resolution: 100, 100 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 2<br>
  YCbCr Positioning: centered<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 160<br>
  Planar Configuration: single image plane<br>
  Software: HP IL v1.1<br>
  YCbCrCoefficients: 0.299000,0.587000,0.114000<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 8<br>
  JpegInterchangeFormatLength: 4608<br>
  JpegQTables: 34 103 103<br>
  JpegDcTables: 172 205 205<br>
  JpegAcTables: 238 421 421<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
<br>
</code></pre>
<h3>221209eb0a273029efa18f4c61f6628a.tif</h3>

<ul><li>Origin: <code>http://drgarywilson.com/images/googlemap.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x3ed7c (257404)<br>
  Image Width: 500 Image Length: 396<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Sample Format: unsigned integer<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;unassoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 65<br>
  Planar Configuration: single image plane<br>
  Software: Pixelmator 1.1.4<br>
  DateTime: 2008-06-16 16:39:39 <br>
  RichTIFFIPTC Data: &lt;present&gt;, 36 bytes<br>
  EXIFIFDOffset: 0x8<br>
  ICC Profile: &lt;present&gt;, 3880 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x8 (8)<br>
  ColorSpace: 1<br>
  PixelXDimension: 500<br>
  PixelYDimension: 396<br>
<br>
</code></pre>
<h3>m1-26f459b3eb2a285626b849d6950db7ab.tif</h3>

<ul><li>Origin: <code>http://lexicon.ff.cuni.cz/tiff/oi_zoega/b0244.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>m1-2743db7c68f091ddc61dcd582febff2d.tif</h3>

<ul><li>Origin: <code>http://211.157.104.92/books/xx/2001/0148/003/00214615/000001.tif</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>27d40bc5f25d8382b890766accb28cf7.tif</h3>

<ul><li>Origin: <code>http://www.swisswater.info/download/aquaclic-clima/clima-brausen-diverse-quadratisch.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x1dbd21 (1948961)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1110 Image Length: 1110<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: separated<br>
  Extra Samples: 1&lt;unassoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 5<br>
  Rows/Strip: 2<br>
  Planar Configuration: single image plane<br>
  ImageDescription: image description                <br>
  Predictor: horizontal differencing 2 (0x2)<br>
<br>
</code></pre>
<h3>m1-299787ea764c0a88bc481364eded5556.tif</h3>

<h3>m2-299787ea764c0a88bc481364eded5556.tif</h3>

<h3>m3-299787ea764c0a88bc481364eded5556.tif</h3>

<h3>m4-299787ea764c0a88bc481364eded5556.tif</h3>

<h3>m5-299787ea764c0a88bc481364eded5556.tif</h3>

<h3>m6-299787ea764c0a88bc481364eded5556.tif</h3>

<h3>m7-299787ea764c0a88bc481364eded5556.tif</h3>

<h3>m8-299787ea764c0a88bc481364eded5556.tif</h3>

<ul><li>Origin: <code>http://www.theprosadvantage.com/client_content/listings/docs/18920-sellersdisclosure.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Subfile Type: multi-page document (8126466 = 0x7c0002)<br>
  Image Width: 1728 Image Length: 1087<br>
  Resolution: 204, 98<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1087<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-9<br>
  Software: NaturalFax<br>
  DateTime: 2008w09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x10232 (66098)<br>
  Image Width: 1728 Image Length: 1089<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 12387393<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x15fda (90074)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1090<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1090<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-14601<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x1f054 (127060)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1089<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1089<br>
  Planar Configuration: single image plane<br>
  Page Number: 3-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x291a2 (168354)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1086<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1086<br>
  Planar Configuration: single image plane<br>
  Page Number: 4-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:0:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x3097a (199034)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1090<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1077<br>
  Planar Configuration: single image plane<br>
  Page Number: 5-9<br>
  Software: NaturalFax<br>
  DateTime: �008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x37e74 (228980)<br>
  Image Width: 1728 Image Length: 1086<br>
  Resolution: 204, 98<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1086<br>
  Planar Configuration: single image plane<br>
  Page Number: 6-9<br>
  Software: NaturalFaxe<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
m2-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Subfile Type: multi-page document (8126466 = 0x7c0002)<br>
  Image Width: 1728 Image Length: 1087<br>
  Resolution: 204, 98<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1087<br>
  Planar Configuration: single image plane<br>
  Page Number: 1536-9<br>
  DateTime: 2008w09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x10232 (66098)<br>
  Image Width: 1728 Image Length: 1089<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 12387393<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:0Z:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x15fda (90074)<br>
  Image Width: 1728 Image Length: 1090<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1090<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-14601<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x1f054 (127060)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1089<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1089<br>
  Planar Configuration: single image plane<br>
  Page Number: 3-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x291a2 (168354)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1086<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1086<br>
  Planar Configuration: single image plane<br>
  Page Number: 4-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:0:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
m3-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1547 Image Length: 1087<br>
  Resolution: 0, 98 pixels/inch<br>
  Compression Scheme: None<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1087<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-9<br>
  Software: <br>
  DateTime: 2�08:09:08 09:42:29<br>
m4-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Image Width: 1728 Image Length: 1087<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1087<br>
  Planar Configuration: single image plane<br>
  Software: NaturalFax�<br>
  DateTime: 2008:09:08 09:42�29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
m5-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1087<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: 28163 (0x6e03)<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1087<br>
  Planar Configuration: single image plane<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
TIFF Directory at offset 0x10232 (66098)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1089<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1089<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-9<br>
  Software: Nat[ralFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
m6-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Image Width: 1728 Image Length: 1087<br>
  Resolution: 204, 2.46466e-08 pixels/inch<br>
  Position: 5, 0<br>
  Bits/Sample: 1<br>
  Compression Scheme: 28163 (0x6e03)<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1087<br>
  Planar Configuration: single image plane<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
m7-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1087<br>
  Resolution: 204, 0 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x10232 (66098)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1089<br>
  Resolution: 204, 98<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1089<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-9<br>
  Software: NaturalFax<br>
  DateTime: <br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
TIFF Directory at offset 0x15fda (90074)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1090<br>
  Resolution: 204, 0.0127588 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1090<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-9<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x1f054 (127060)<br>
  Image Width: 1728 Image Length: 1089<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1089<br>
  Planar Configuration: single image plane<br>
  Software: NaturalFax<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
m8-299787ea764c0a88bc481364eded5556.tif:<br>
TIFF Directory at offset 0x9fec (40940)<br>
  Image Width: 1728 Image Length: 1087<br>
  Resolution: 204, 0 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1087<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-9<br>
  Software: NaturalFax<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0x10232 (66098)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1089<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1089<br>
  Planar Configuration: single image plane<br>
  DateTime: 2008:09:08 09:42:29<br>
  Group 3 Options: 2-d encoding+EOL padding (5 = 0x5)<br>
  Fax Data: clean (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
<br>
</code></pre>
<h3>2b27b742e68d313d5ea4abd7847cbff4.tif</h3>

<ul><li>Origin: <code>http://mp3.news.com.au/bcm/romastreet.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3432 Image Length: 2394<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2400<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 368<br>
  JpegInterchangeFormatLength: 507201<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x7becc (507596)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3426 Image Length: 2380<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 507956<br>
  JpegInterchangeFormatLength: 516472<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0xfa1c4 (1024452)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3414 Image Length: 2380<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 1024812<br>
  JpegInterchangeFormatLength: 400675<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x15c068 (1425512)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3422 Image Length: 2378<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 1425872<br>
  JpegInterchangeFormatLength: 349876<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x1b189c (1775772)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3426 Image Length: 2376<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2376<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 1776132<br>
  JpegInterchangeFormatLength: 364728<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x20aad4 (2140884)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3396 Image Length: 2376<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2376<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 2141244<br>
  JpegInterchangeFormatLength: 561210<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x293c90 (2702480)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3418 Image Length: 2386<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2392<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 2702840<br>
  JpegInterchangeFormatLength: 569066<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x31ecfc (3271932)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3426 Image Length: 2384<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 3272292<br>
  JpegInterchangeFormatLength: 554385<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x3a6410 (3826704)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3418 Image Length: 2378<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 3827064<br>
  JpegInterchangeFormatLength: 542052<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x42aaf4 (4369140)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3402 Image Length: 2380<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 4369500<br>
  JpegInterchangeFormatLength: 403762<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x48d5a8 (4773288)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3426 Image Length: 2394<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2400<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 4773648<br>
  JpegInterchangeFormatLength: 382099<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x4eabbc (5155772)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3422 Image Length: 2382<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 5156132<br>
  JpegInterchangeFormatLength: 371374<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x5457ec (5527532)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3414 Image Length: 2382<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 5527892<br>
  JpegInterchangeFormatLength: 354829<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x59c37c (5882748)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3422 Image Length: 2378<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 5883108<br>
  JpegInterchangeFormatLength: 369771<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x5f6968 (6252904)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3418 Image Length: 2380<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 6253264<br>
  JpegInterchangeFormatLength: 363254<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x64f5e0 (6616544)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3394 Image Length: 2374<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2376<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 6616904<br>
  JpegInterchangeFormatLength: 356390<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x6a6788 (6973320)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3422 Image Length: 2380<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 6973680<br>
  JpegInterchangeFormatLength: 359661<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x6fe5f8 (7333368)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3422 Image Length: 2378<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 7333728<br>
  JpegInterchangeFormatLength: 461910<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x76f3d0 (7795664)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3418 Image Length: 2374<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2376<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 7796024<br>
  JpegInterchangeFormatLength: 470044<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x7e216c (8266092)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3420 Image Length: 2378<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2384<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 8266452<br>
  JpegInterchangeFormatLength: 355030<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x838dc4 (8621508)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3418 Image Length: 2374<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2376<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 8621868<br>
  JpegInterchangeFormatLength: 424049<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x8a07b8 (9045944)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3420 Image Length: 2374<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2376<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 9046304<br>
  JpegInterchangeFormatLength: 376325<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x8fc740 (9422656)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3394 Image Length: 2368<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2368<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.07.00<br>
  JpegInterchangeFormat: 9423016<br>
  JpegInterchangeFormatLength: 653552<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
<br>
</code></pre>
<h3>m1-336db1cd76254717eb50a8602b651fbf.tif</h3>

<h3>m2-336db1cd76254717eb50a8602b651fbf.tif</h3>

<h3>m3-336db1cd76254717eb50a8602b651fbf.tif</h3>

<h3>m4-336db1cd76254717eb50a8602b651fbf.tif</h3>

<h3>m5-336db1cd76254717eb50a8602b651fbf.tif</h3>

<h3>m6-336db1cd76254717eb50a8602b651fbf.tif</h3>

<h3>m7-336db1cd76254717eb50a8602b651fbf.tif</h3>

<h3>m8-336db1cd76254717eb50a8602b651fbf.tif</h3>

<ul><li>Origin: <code>http://li.ru/go?www.kbural.ru/files/petrostil.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-336db1cd76254717eb50a8602b651fbf.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Image Width: 2306 Image Length: 3111<br>
  Resolution: 300, 0<br>
  Compression Scheme: 198 (0xc6)<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 28<br>
  Planar Configuration: single image plane<br>
  Photoshop Data: &lt;present&gt;, 4598 bytes<br>
m2-336db1cd76254717eb50a8602b651fbf.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2306 Image Length: 3111<br>
  Resolution: 0.608069, 0 pixels/inch<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 1<br>
  Planar Configuration: single image plane<br>
  Software: <br>
  Photoshop Data: &lt;present&gt;, 4598 bytes<br>
  Predictor: none 1 (0x1)<br>
m3-336db1cd76254717eb50a8602b651fbf.tif:<br>
m4-336db1cd76254717eb50a8602b651fbf.tif:<br>
m5-336db1cd76254717eb50a8602b651fbf.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2306 Image Length: 3111<br>
  Resolution: 300, 300 pixels/inch<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 28<br>
  Planar Configuration: single image plane<br>
  Photoshop Data: &lt;present&gt;, 4598 bytes<br>
  Predictor: none 1 (0x1)<br>
m6-336db1cd76254717eb50a8602b651fbf.tif:<br>
m7-336db1cd76254717eb50a8602b651fbf.tif:<br>
m8-336db1cd76254717eb50a8602b651fbf.tif:<br>
<br>
</code></pre>
<h3>m1-3562055aecf63b573f8a18c4034a4a23.tif</h3>

<h3>m2-3562055aecf63b573f8a18c4034a4a23.tif</h3>

<ul><li>Origin: <code>http://lexicon.ff.cuni.cz/tiff/goth_balg/b0350.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-3562055aecf63b573f8a18c4034a4a23.tif:<br>
TIFF Directory at offset 0x10ae4 (68324)<br>
  Image Width: 2653 Image Length: 3379<br>
  Resolution: 118.12, 0<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Planar Configuration: single image plane<br>
  DocumentName: gothic_tiffs//B350.tiff<br>
m2-3562055aecf63b573f8a18c4034a4a23.tif:<br>
TIFF Directory at offset 0x10ae4 (68324)<br>
  Image Width: 2653 Image Length: 3379<br>
  Resolution: 118.12, 0<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Orientation: row 0 top, col 0 lhs<br>
  Rows/Strip: 3430<br>
  Planar Configuration: single image plane<br>
  DocumentName: gothic_ti�fs//B350.tiff<br>
  Software: Z(#)ImageMagick 5.3.0 04/01/01 Q:16 http://www.imagemagick.kro<br>
<br>
</code></pre>
<h3>356a619433db27fb412ec6fef583eded.tif</h3>

<ul><li>Origin: <code>http://planning.babergh.gov.uk/doldp/4318_7.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0xe3ca4 (933028)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2338 Image Length: 1656<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 2<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 1656<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 938146<br>
  Software:  HATFILT Version 1.8  <br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 8<br>
  JpegInterchangeFormatLength: 932928<br>
TIFF Directory at offset 0x1ab9e4 (1751524)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2338 Image Length: 1656<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 2<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 1656<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 1756230<br>
  Software:  HATFILT Version 1.8  <br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 938308<br>
  JpegInterchangeFormatLength: 813124<br>
<br>
</code></pre>
<h3>362323f81c0160afd677241cd5ce92e9.tif</h3>

<ul><li>Origin: <code>https://apps3.suffolkcoastal.gov.uk/planningonlinedocuments/77790_2.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1275 Image Length: 1755<br>
  Resolution: 150, 150<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 1<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-4<br>
  Make: Hewlett-Packard<br>
  Model: WIA-HP Scanjet 3800<br>
  Software: Onstream Trapeze 6.16<br>
  DateTime: 2007:11:19 10:17:09<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 486<br>
  JpegInterchangeFormatLength: 282580<br>
  JpegQTables: 518 583 583<br>
  JpegDcTables: 671 697 697<br>
  JpegAcTables: 719 822 822<br>
  JpegProc: 1<br>
TIFF Directory at offset 0x451ba (283066)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 970 Image Length: 1546<br>
  Resolution: 150, 150<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 1<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-4<br>
  Make: Hewlett-Packard<br>
  Model: WIA-HP Scanjet 3800<br>
  Software: Onstream Trapeze 6.16<br>
  DateTime: 2007:11:19 10:18:06<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 283544<br>
  JpegInterchangeFormatLength: 383350<br>
  JpegQTables: 283576 283641 283641<br>
  JpegDcTables: 283729 283755 283755<br>
  JpegAcTables: 283778 283884 283884<br>
  JpegProc: 1<br>
TIFF Directory at offset 0xa2d0e (666894)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1275 Image Length: 1755<br>
  Resolution: 150, 150<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 1<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-4<br>
  Make: Hewlett-Packard<br>
  Model: WIA-HP Scanjet 3800<br>
  Software: Onstream Trapeze 6.16<br>
  DateTime: 2007:11:19 10:18:40<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 667372<br>
  JpegInterchangeFormatLength: 414823<br>
  JpegQTables: 667404 667469 667469<br>
  JpegDcTables: 667557 667583 667583<br>
  JpegAcTables: 667605 667708 667708<br>
  JpegProc: 1<br>
TIFF Directory at offset 0x108354 (1082196)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1275 Image Length: 1755<br>
  Resolution: 150, 150<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 1<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  Page Number: 3-4<br>
  Make: Hewlett-Packard<br>
  Model: WIA-HP Scanjet 3800<br>
  Software: Onstream Trapeze 6.16<br>
  DateTime: 2007:11:19 10:19:05<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 1082674<br>
  JpegInterchangeFormatLength: 307665<br>
  JpegQTables: 1082706 1082771 1082771<br>
  JpegDcTables: 1082859 1082884 1082884<br>
  JpegAcTables: 1082905 1083009 1083009<br>
  JpegProc: 1<br>
<br>
</code></pre>
<h3>3755b21390a93c1474aef88f4162de17.tif</h3>

<ul><li>Origin: <code>http://preferredlandscapetx.com/goliveimages/cert_arb.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x41126 (266534)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 646 Image Length: 1126<br>
  Resolution: 96, 96 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;unassoc-alpha&gt;<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 4<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop 7.0<br>
  DateTime: 2003:06:16 13:16:16<br>
  Dot Range: 0-255<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 6532 bytes<br>
  EXIFIFDOffset: 0x351304<br>
  Predictor: none 1 (0x1)<br>
<br>
</code></pre>
<h3>m1-3c6b71d657852e13d0b5dfc0906343f5.tif</h3>

<ul><li>Origin: <code>http://www.zunior.com/dropzone/thevioletarchers_bandphoto1.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Image Width: 1745 Image Length: 1309<br>
  Resolution: 0, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  Make: Canon<br>
  Model: Canon EOS�20D<br>
  Software: QuickTime 7.1.3<br>
  HostComputer: Mac OS X10.4.7<br>
  EXIFIFDOffset: 0x2c8c<br>
  ICC Profile: &lt;present&gt;, 560 bytes<br>
TIFF Directory at offset 0x2c8c (11404)<br>
  ExposureTime: 0.004000<br>
  ExposureProgram: 86<br>
  ISOSpeedRatings: 100<br>
  ExifVersion: 0x30,0x32,0x32,0x30<br>
  DateTimeOriginal: 2008:04:13 13:34:15<br>
  DateTimeDigitized: 2008:04:13 13:34:15<br>
  ApertureValue: 0.854529<br>
  ExposureBiasValue: 0.000000<br>
  MaxApertureValue: 2.968750<br>
  MeteringMode: 6<br>
  Flash: 9<br>
  FocalLength: 18.000000<br>
<br>
</code></pre>
<h3>m1-3ca2fd64c710a30edb60987e74d405cf.tif</h3>

<h3>m2-3ca2fd64c710a30edb60987e74d405cf.tif</h3>

<ul><li>Origin: <code>http://files.dnr.state.mn.us/lakefind/data/lakemaps/c1185010.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-3ca2fd64c710a30edb60987e74d405cf.tif:<br>
m2-3ca2fd64c710a30edb60987e74d405cf.tif:<br>
<br>
</code></pre>
<h3>401d27e0565674c24a017588b8cd61d2.tif</h3>

<ul><li>Origin: <code>http://www.convisual.com/img/presse/handy/dwnld/austin_6630_300_hr.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 928 Image Length: 1772<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;unspecified&gt;<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 2<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop Elements 2.0<br>
  DateTime: 2005:01:24 11:05:43<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 15730 bytes<br>
  EXIFIFDOffset: 0x25724c<br>
  ICC Profile: &lt;present&gt;, 560 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x25724c (2454092)<br>
  ExposureTime: 8.000000<br>
  FNumber: 20.000000<br>
  ExposureProgram: 1<br>
  ISOSpeedRatings: 100<br>
  DateTimeOriginal: 2004:04:26 13:55:57<br>
  DateTimeDigitized: 2004:04:26 13:55:57<br>
  ShutterSpeedValue: -3.000000<br>
  ApertureValue: 8.625000<br>
  ExposureBiasValue: 0.000000<br>
  MeteringMode: 5<br>
  Flash: 0<br>
  FocalLength: 90.000000<br>
  ColorSpace: 65535<br>
  PixelXDimension: 928<br>
  PixelYDimension: 1772<br>
  FocalPlaneXResolution: 2886.363525<br>
  FocalPlaneYResolution: 2885.805664<br>
  FocalPlaneResolutionUnit: 2<br>
  CustomRendered: 0<br>
  ExposureMode: 1<br>
  WhiteBalance: 0<br>
  SceneCaptureType: 0<br>
<br>
</code></pre>
<h3>m10-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m11-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m12-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m13-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m1-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m14-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m15-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m16-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m17-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m18-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m2-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m3-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m4-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m5-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m6-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m7-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m8-42c19f8e79e582bef107f372f18a074b.tif</h3>

<h3>m9-42c19f8e79e582bef107f372f18a074b.tif</h3>

<ul><li>Origin: <code>http://csi.nfshost.com/wp-content/icon-3.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>m10-42c19f8e79e582bef107f372f18a074b.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 17 Image Length: 45585<br>
  Resolution: 72.009, 72.009 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;assoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 17<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Pho�oshop CS3 Macintosh<br>
  DateTime: <br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  EXIFIFDOffset: 0x739c<br>
  ICC Profile: &lt;present&gt;, 4380 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x739c (29596)<br>
  ColorSpace: 13311<br>
  PixelXDimension: 17<br>
  PixelYDimension: 17<br>
m11-42c19f8e79e582bef107f372f18a074b.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 17 Image Length: 17<br>
  Resolution: 72.009, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;assoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 17<br>
  Planar Configuration: single image plane<br>
  DateTime: 2008:06:13 10:53:40<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 8920 bytes<br>
  ICC Profile: &lt;present&gt;, 4380 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
m12-42c19f8e79e582bef107f372f18a074b.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Image Width: 17 Image Length: 17<br>
  Resolution: 72.009, 72.009 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;assoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 17<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop CS3 Macintosh<br>
  DateTime: 2008:06:13 10:53:40<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 8920 bytes<br>
  EXIFIFDOffset: 0x739c<br>
  ICC Profile: &lt;present&gt;, 4380 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x739c (29596)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 17<br>
  PixelYDimension: 17<br>
m13-42c19f8e79e582bef107f372f18a074b.tif:<br>
m1-42c19f8e79e582bef107f372f18a074b.tif:<br>
m14-42c19f8e79e582bef107f372f18a074b.tif:<br>
m15-42c19f8e79e582bef107f372f18a074b.tif:<br>
m16-42c19f8e79e582bef107f372f18a074b.tif:<br>
m17-42c19f8e79e582bef107f372f18a074b.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 17 Image Length: 17<br>
  Resolution: 72.009, 72.009<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;assoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 17<br>
  Planar Configuration: single image plane<br>
  DateTime: 2008:06:13 10:53:40<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 8920 bytes<br>
  EXIFIFDOffset: 0x739c<br>
  ICC Profile: &lt;present&gt;, 4380 bytes<br>
<br>
</code></pre>
<h3>434cb1e9680e3b4eda7f4dd430bcd2bf.tif</h3>

<ul><li>Origin: <code>http://vss01.narod.ru/files/6sem/sessiya_6sem.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2147 Image Length: 1027<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: palette color (RGB from colormap)<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 3<br>
  Planar Configuration: single image plane<br>
  Color Map: (present)<br>
  Make: CASIO<br>
  Model: QV-4000  <br>
  Software: Adobe Photoshop 7.0<br>
  DateTime: 2004:05:25 11:58:16<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 5184 bytes<br>
  EXIFIFDOffset: 0x58db8<br>
  ICC Profile: &lt;present&gt;, 3144 bytes<br>
  Predictor: none 1 (0x1)<br>
TIFF Directory at offset 0x58db8 (363960)<br>
  ExposureTime: 0.040000<br>
  FNumber: 2.300000<br>
  ExposureProgram: 1<br>
  ExifVersion: 0x30,0x32,0x31,0x30<br>
  DateTimeOriginal: 2004:05:25 08:16:46<br>
  DateTimeDigitized: 2004:05:25 08:16:46<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  CompressedBitsPerPixel: 4.012406<br>
  ExposureBiasValue: 0.000000<br>
  MaxApertureValue: 2.000000<br>
  MeteringMode: 5<br>
  Flash: 1<br>
  FocalLength: 11.760000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 1<br>
  PixelXDimension: 2147<br>
  PixelYDimension: 1027<br>
<br>
</code></pre>
<h3>m1-487f40372de5a8b6c848ba2569848492.tif</h3>

<ul><li>Origin: <code>http://lexicon.ff.cuni.cz/tiff/oswed_noreen/b0456.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1235 Image Length: 2128<br>
  Resolution: 296.365, 0.352634<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: 21248 (0x5300)<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 52<br>
  Planar Configuration: single image plane<br>
  DateTime: 2003:10:06 15:�4:52<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 16492 bytes<br>
  EXIFIFDOffset: 0x1e190<br>
<br>
</code></pre>
<h3>48af30b09e42ec73f206ce1ac09a424b.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x1bffc (114684)<br>
  Image Width: 333 Image Length: 225<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 16<br>
  Sample Format: signed integer<br>
  Compression Scheme: SGILog<br>
  Photometric Interpretation: CIE Log2(L) (u',v')<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 8<br>
  Planar Configuration: single image plane<br>
  Sample to Nits conversion factor: 1.7900e+02<br>
<br>
</code></pre>
<h3>m1-4a7d8e5153957beadcd49c6f540aab78.tif</h3>

<ul><li>Origin: <code>http://www.angelfire.com/ak3/ahti3/images/aita.tif</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>54743a2a36ef90c7ed8bb5da8b6ebaf4.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x34226 (213542)<br>
  Image Width: 512 Image Length: 384<br>
  Position: 0, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 5<br>
  Planar Configuration: single image plane<br>
<br>
</code></pre>
<h3>m1-5512ff2fc91566c07c8c8d3fd352a731.tif</h3>

<ul><li>Origin: <code>http://www.infodez.ru/production/_oborud/destruktor_etna-497/destruktor_etna-ru-020919.tif</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>551adc8ce6c3c9cc59040903b0428f47.tif</h3>

<ul><li>Origin: <code>http://n2.nabble.com/attachment/2048472/0/slope_rgb_dfl_tls.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Image Width: 190 Image Length: 143<br>
  Tile Width: 256 Tile Length: 256<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Sample Format: unsigned integer<br>
  Compression Scheme: AdobeDeflate<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  DocumentName: /home/shoofi/slope.tif<br>
  Predictor: none 1 (0x1)<br>
<br>
</code></pre>
<h3>5dd2583cd54384e56a769f04ea05c999.tif</h3>

<ul><li>Origin: <code>http://gerb.murman.ru/tif/region_2004.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 600 Image Length: 802<br>
  Resolution: 118.11, 118.11 pixels/cm<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;assoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 109<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop CS2 Windows<br>
  DateTime: 2006:06:15 20:50:55<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 8084 bytes<br>
  EXIFIFDOffset: 0x34c98<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x34c98 (216216)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 600<br>
  PixelYDimension: 802<br>
<br>
</code></pre>
<h3>m1-62804e47400d6a0fd233c32ea8db4e48.tif</h3>

<ul><li>Origin: <code>http://gfx.ip-sprachreisen.de/presse/exmouth_beach_hi_res.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1000 Image Length: 667<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 16<br>
  Compression Scheme: None<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 667<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 5906976<br>
  Make: Canon<br>
  Model: Canon EOS 20D<br>
  Software: Adobe Photoshop 7.0<br>
  Dot Range: 0-65535<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 5050 bytes<br>
  EXIFIFDOffset: 0x5a1f70<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
TIFF Directory at offset 0x5a1f70 (5906288)<br>
  ExposureTime: 0.001250<br>
  FNumber: 6.300000<br>
  ExposureProgram: 3<br>
  ISOSpeedRatings: 100<br>
  ExifVersion: 0x30,0x32,0x32,0x31<br>
  DateTimeOriginal: 2006:07:09 16:39:54<br>
  DateTimeDigitized: 2006:07:09 16:39:54<br>
  ComponentsConfiguration: 0x0,0x0,0x0,0x0<br>
  ShutterSpeedValue: 9.643860<br>
  ApertureValue: 5.310699<br>
  ExposureBiasValue: 0.000000<br>
  MeteringMode: 5<br>
  Flash: 16<br>
  FocalLength: 55.000000<br>
  FlashpixVersion: 0x30,0x31,0x30,0xd8<br>
  ColorSpace: 65535<br>
  PixelXDimension: 1000<br>
  PixelYDimension: 667<br>
  FocalPlaneXResolution: 3959.322021<br>
  FocalPlaneYResolution: 3959.322021<br>
  FocalPlaneResolutionUnit: 2<br>
  CustomRendered: 0<br>
  ExposureMode: 0<br>
  WhiteBalance: 0<br>
  SceneCaptureType: 0<br>
<br>
</code></pre>
<h3>m1-63c8b14ea08a18c884d05a3431716047.tif</h3>

<h3>m2-63c8b14ea08a18c884d05a3431716047.tif</h3>

<h3>m3-63c8b14ea08a18c884d05a3431716047.tif</h3>

<h3>m4-63c8b14ea08a18c884d05a3431716047.tif</h3>

<h3>m5-63c8b14ea08a18c884d05a3431716047.tif</h3>

<h3>m6-63c8b14ea08a18c884d05a3431716047.tif</h3>

<ul><li>Origin: <code>http://lis.ly.gov.tw/npl/commun/58/3.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-63c8b14ea08a18c884d05a3431716047.tif:<br>
m2-63c8b14ea08a18c884d05a3431716047.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1433 Image Length: 2023<br>
  Resolution: 200, 200<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2023<br>
  Planar Configuration: single image plane<br>
  DateTime: 2005.09.15 16:28:54<br>
m3-63c8b14ea08a18c884d05a3431716047.tif:<br>
m4-63c8b14ea08a18c884d05a3431716047.tif:<br>
m5-63c8b14ea08a18c884d05a3431716047.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1433 Image Length: 2023<br>
  Resolution: 200, 200<br>
  Bits/Sample: 1<br>
  Compression Scheme: None<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2023<br>
  Planar Configuration: single image plane<br>
  Software: Fu�i Xerox Co., Ltd. Raster S�pport Toolkit Version 2.3<br>
  DateTime: 2005.09.15 16:28:54<br>
m6-63c8b14ea08a18c884d05a3431716047.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1433 Image Length: 2023<br>
  Resolution: 200, 200<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2023<br>
  Planar Configuration: single image plane<br>
  Software: Fu�i Xerox Co., Ltd. Raster S�pport Toolkit Version 2.3<br>
  DateTime: 2005.09.15 16:28:54<br>
<br>
</code></pre>
<h3>6453732434a8a2358a3c895d962bdce2.tif</h3>

<ul><li>Origin: <code>http://www.sparetimelabs.com/test-out.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 200 Image Length: 200<br>
  Tile Width: 128 Tile Length: 128<br>
  Resolution: 20, 20 pixels/cm<br>
  Bits/Sample: 8<br>
  Compression Scheme: PackBits<br>
  Photometric Interpretation: RGB color<br>
  Extra Samples: 1&lt;assoc-alpha&gt;<br>
  Samples/Pixel: 4<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop 7.0<br>
  DateTime: 2005:01:22 08:13:44<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 3888 bytes<br>
  EXIFIFDOffset: 0x22c8<br>
TIFF Directory at offset 0x22c8 (8904)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 200<br>
  PixelYDimension: 200<br>
<br>
</code></pre>
<h3>m1-68bc8a1966db7a1da2d3b5946c00d1af.tif</h3>

<ul><li>Origin: <code>http://www.nhicb.gov.tw/nhicbj00/tif/0000000319.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Image Width: 3306 Image Length: 2368<br>
  Resolution: 200, 0.0052082 pixels/inch<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 76<br>
  Planar Configuration: single image plane<br>
  Ink Set: CMYK<br>
  Software: Oi/GFS, writer v00.06.02<br>
  Group 4 Options: (0 = 0x0)<br>
<br>
</code></pre>
<h3>6cd02db6f3688efdd705c28ffcb9a3d3.tif</h3>

<ul><li>Origin: <code>http://www.rootsweb.com/~irlcav/moy.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 7465 Image Length: 5536<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: (infinite)<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-1<br>
  Make: Oce <br>
  Model: 9400  <br>
  Software: Imagenation VME<br>
  Group 4 Options: (0 = 0x0)<br>
<br>
</code></pre>
<h3>7324fcaff3aad96f27899da51c1bb5d9.tif</h3>

<ul><li>Origin: <code>http://www.luotain.uku.fi/~kraka/uudet_sivut/data/pressi/kraka_pressi02.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 4064 Image Length: 2487<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: AdobeDeflate<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 86<br>
  Planar Configuration: single image plane<br>
  Make: Canon<br>
  Model: Canon EOS-1DS<br>
  Software: Adobe Photoshop CS Windows<br>
  DateTime: 2004:06:13 17:44:48<br>
  Artist: Studio Mantyniemi<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 32 bytes<br>
  Photoshop Data: &lt;present&gt;, 126558 bytes<br>
  EXIFIFDOffset: 0xe73c6c<br>
  ICC Profile: &lt;present&gt;, 560 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0xe73c6c (15154284)<br>
  ExposureTime: 0.016667<br>
  FNumber: 18.000000<br>
  ISOSpeedRatings: 100<br>
  ExifVersion: 0x30,0x32,0x32,0x30<br>
  DateTimeOriginal: 2003:11:25 16:05:53<br>
  DateTimeDigitized: 2003:11:25 16:05:53<br>
  ShutterSpeedValue: 6.000000<br>
  ApertureValue: 8.375000<br>
  ExposureBiasValue: 0.000000<br>
  FocalLength: 63.000000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 65535<br>
  PixelXDimension: 4064<br>
  PixelYDimension: 2487<br>
  FocalPlaneXResolution: 2886.363525<br>
  FocalPlaneYResolution: 2885.805664<br>
  FocalPlaneResolutionUnit: 2<br>
  CustomRendered: 0<br>
  ExposureMode: 1<br>
  WhiteBalance: 1<br>
  SceneCaptureType: 0<br>
<br>
</code></pre>
<h3>m10-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m11-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m12-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m1-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m2-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m3-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m4-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m5-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m6-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m7-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m8-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<h3>m9-76c43508fc007bcf5902b6a28e8055a5.tif</h3>

<ul><li>Origin: <code>http://www.swr.de/presseservice/logos/swr2/-/id=228486/property=download/nid=4084/zpjqve/index.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m10-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: transparency mask (228 = 0xe4)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 706.323, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photoshop 7.0<br>
  Dot Range: 0-255<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
  PixelYDimension: 1313<br>
m11-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: transparency mask (228 = 0xe4)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 706.323, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photoshop 7.0<br>
  Dot Range: 0-255<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
  PixelYDimension: 1313<br>
m12-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: transparency mask (228 = 0xe4)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 706.323, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 79<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Phoos�op 7.0<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
m1-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: transparency mask (228 = 0xe4)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 706.323, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: esc="CR"?&gt;<br>
&lt;x:xapmeH<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
m2-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: transparency mask (228 = 0xe4)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 0, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photoshop 7.0<br>
  Dot Range: 0-255<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
  PixelYDimension: 1313<br>
m3-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photoshop 7.0<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc7280<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
m4-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: transparency mask (228 = 0xe4)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 706.323, 300 pixels/inch<br>
  Bits/Sample: 8224<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photos�op 7.0<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
m5-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: transparency mask (228 = 0xe4)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 706.323, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photos�op 7.0<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
m6-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 300, 0.962106 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop 7.0<br>
  Dot Range: 0-255<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
  Predictor: 60162 (0xeb02)<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 671090412<br>
  PixelYDimension: 1313<br>
m7-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 300, 300<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photoshop 7.0<br>
  Dot Range: 0-255<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
  Predictor: 60162 (0xeb02)<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 1772<br>
  PixelYDimension: 1313<br>
m8-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 300, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photoshop 7.0<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
  ICC Profile: &lt;present&gt;, 557164 bytes<br>
  Predictor: 60315 (0xeb9b)<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 1772<br>
  PixelYDimension: 1313<br>
m9-76c43508fc007bcf5902b6a28e8055a5.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (14080 = 0x3700)<br>
  Image Width: 1772 Image Length: 1313<br>
  Resolution: 300, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  ImageDescription: <br>
  Software: Adobe Photoshor 7.0<br>
  Dot Range: 0-255<br>
  Photoshop Data: &lt;present&gt;, 5840 bytes<br>
  EXIFIFDOffset: 0xc8e80<br>
  Predictor: 60162 (0xeb02)<br>
TIFF Directory at offset 0xc8e80 (822912)<br>
  PixelYDimension: 1313<br>
<br>
</code></pre>
<h3>m1-76d5d8fd02d58b774f2bae6f7b763e3e.tif</h3>

<h3>m2-76d5d8fd02d58b774f2bae6f7b763e3e.tif</h3>

<h3>m3-76d5d8fd02d58b774f2bae6f7b763e3e.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>m1-79818c280a08c94bf7fd2a54b1e2567d.tif</h3>

<ul><li>Origin: <code>http://www.geocities.com/jwhicks53705/cem_map.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2500 Image Length: 3225<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: None<br>
  Photometric Interpretation: min-is-black<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 26<br>
  Planar Configuration: single image plane<br>
<br>
</code></pre>
<h3>m1-8110934bb3b18d0e87ccc1ddfc5f0107.tif</h3>

<ul><li>Origin: <code>ftp://ftp.cordis.europa.eu/pub/paxis/docs/open_space_conference.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x3b94 (15252)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0xb05a (45146)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Sample Format: void<br>
  Compression Scheme: None<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
TIFF Directory at offset 0x251c6 (152006)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x3442c (214060)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x4cf20 (315168)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x5edea (388586)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x79810 (497680)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x8e01e (581662)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3307 Image Length: 4704<br>
  Resolution: 400, 400 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 4704<br>
  Planar Configuration: single image plane<br>
  Group 4 Options: (0 = 0x0)<br>
<br>
</code></pre>
<h3>84399cc32c29ac0cf33b96a0f654f379.tif</h3>

<ul><li>Origin: <code>http://larsdoornbos.com/zoom.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 3300 Image Length: 3508<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 1, 1<br>
  YCbCr Positioning: cosited<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 6<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop 7.0<br>
  DateTime: 2006:06:08 14:55:36<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 15828 bytes<br>
  EXIFIFDOffset: 0xaf3748<br>
  JPEG Tables: (558 bytes)<br>
TIFF Directory at offset 0xaf3748 (11482952)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 3300<br>
  PixelYDimension: 3508<br>
<br>
</code></pre>
<h3>m1-84da94dc7e5469f7849b0a7efdff5462.tif</h3>

<ul><li>Origin: <code>http://talks.mark-itt.ru/forums/icons/forum_pictures/000556/556923.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x372e32 (3616306)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1754 Image Length: 2481<br>
  Resolution: 150, 150 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: separated<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 2<br>
  Planar Configuration: single image plane<br>
  ImageDescription: image description<br>
  Predictor: horizontal differencing 2 (0x2)<br>
<br>
</code></pre>
<h3>89b5888641d5910e92bf451b5e639ad0.tif</h3>

<ul><li>Origin: <code>http://4praise.com/cgi-bin/files/sm/380.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x48 (72)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 766 Image Length: 991<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 8<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
  JpegInterchangeFormat: 444<br>
  JpegInterchangeFormatLength: 601<br>
  JpegQTables: 8665 8734 8734<br>
  JpegDcTables: 8822 9038 9038<br>
  JpegAcTables: 8855 9071 9071<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x17a8c (96908)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 766 Image Length: 991<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 1<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 8<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
  JpegInterchangeFormat: 97280<br>
  JpegInterchangeFormatLength: 601<br>
  JpegQTables: 169533 169602 169602<br>
  JpegDcTables: 169690 169906 169906<br>
  JpegAcTables: 169723 169939 169939<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
<br>
</code></pre>
<h3>8d8582b004aa2560f5bccffbccf4f3d6.tif</h3>

<ul><li>Origin: <code>http://www.biesse.it/dati/files/246_508_master_30_worktable.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0xfe626 (1041958)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 680 Image Length: 510<br>
  Resolution: 72, 72 (unitless)<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 510<br>
  Planar Configuration: single image plane<br>
  Make: Hasselblad/Imacon<br>
  Model: Ixpress 528C - Hasselblad ELD<br>
  RichTIFFIPTC Data: &lt;present&gt;, 92 bytes<br>
  Photoshop Data: &lt;present&gt;, 104 bytes<br>
  EXIFIFDOffset: 0x5c8<br>
  ICC Profile: &lt;present&gt;, 1080 bytes<br>
TIFF Directory at offset 0x5c8 (1480)<br>
  ExposureTime: 0.016667<br>
  ISOSpeedRatings: 50<br>
  ExifVersion: 0x30,0x32,0x31,0x30<br>
  DateTimeOriginal: 2006:09:12 21:04:57<br>
  DateTimeDigitized: 2006:09:12 21:04:57<br>
  ShutterSpeedValue: 5.906890<br>
<br>
</code></pre>
<h3>m1-93456679a773921d30efafd08f3ad542.tif</h3>

<ul><li>Origin: <code>http://www.archive.org/download/usgs_drg_wi_45091_a6/o45091a6.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x450eb0 (4525744)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 4772 Image Length: 6776<br>
  Resolution: 250, 250 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: PackBits<br>
  Photometric Interpretation: palette color (RGB from colormap)<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1<br>
  Planar Configuration: single image plane<br>
  Color Map: (present)<br>
  ImageDescription: @<br>
  DateTime: 1996:11:19 13:58:06<br>
<br>
</code></pre>
<h3>m1-96292a1bd64fec83bb6cdd2480a755b6.tif</h3>

<ul><li>Origin: <code>http://clubvudu.googlegroups.com/web/vudu-embassy-a3.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1169 Image Length: 1654<br>
  Resolution: 0, 100 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: AdobeDeflate<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 896<br>
  Planar Configuration: separate image planes<br>
  Software: Adobe Photoshop CS3 Macintosh<br>
  DateTime: 2007:09:26 16:19:29<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 22290 bytes<br>
  EXIFIFDOffset: 0x2e8018<br>
  ICC Profile: &lt;present&gt;, 3144 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x2e8018 (3047448)<br>
  ColorSpace: 1<br>
  PixelYDimension: 1654<br>
<br>
</code></pre>
<h3>m1-9a47770b40347f842caed33f5baa41df.tif</h3>

<ul><li>Origin: <code>http://www.archive.org/download/usgs_drg_tx_28097_e1/o28097e1.tif</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>9b286add70871bbbef1601997b429344.tif</h3>

<ul><li>Origin: <code>http://www.jyjs.gov.cn/sylj/fgk/20070629a.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x3012 (12306)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1646 Image Length: 2332<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2332<br>
  Planar Configuration: single image plane<br>
  DocumentName: DN0PUnknown serial  1179132224         811000.----!--<br>
  Make: Kodak<br>
  Model: ProductID<br>
  Software: xVCS V3.5      <br>
  DateTime: 2007:05:14 16:44:35<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x9d0c (40204)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1653 Image Length: 2333<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2333<br>
  Planar Configuration: single image plane<br>
  DocumentName: DN0PUnknown serial  1179132224         900000.----!--<br>
  Make: Kodak<br>
  Model: ProductID<br>
  Software: xVCS V3.5      <br>
  DateTime: 2007:05:14 16:44:37<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x100ce (65742)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1653 Image Length: 2329<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2329<br>
  Planar Configuration: single image plane<br>
  DocumentName: DN0PUnknown serial  1179132224         911000.----!--<br>
  Make: Kodak<br>
  Model: ProductID<br>
  Software: xVCS V3.5      <br>
  DateTime: 2007:05:14 16:44:38<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x57cbc (359612)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1641 Image Length: 2317<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 2<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2317<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 365700<br>
  Model: ProductID<br>
  Software: xVCS V3.5      <br>
  DateTime: 2007:05:14 16:44:40<br>
  Artist: IRIS 2001          <br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JpegInterchangeFormat: 66024<br>
  JpegInterchangeFormatLength: 293443<br>
<br>
</code></pre>
<h3>9bd49db0707bb5d7ddeca56b1de28ab8.tif</h3>

<ul><li>Origin: <code>http://www.cestisticalatina.it/public//2009/01/colombo.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1972 Image Length: 2000<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 177<br>
  Planar Configuration: single image plane<br>
  Make: NIKON CORPORATION<br>
  Model: NIKON D200<br>
  Software: Adobe Photoshop CS3 Macintosh<br>
  DateTime: 2009:01:29 14:29:52<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 12394 bytes<br>
  EXIFIFDOffset: 0x2ab44<br>
  ICC Profile: &lt;present&gt;, 560 bytes<br>
<br>
</code></pre>
<h3>a516905c06cbc05e8adac7b0b7e4f514.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x32fee (208878)<br>
  Image Width: 512 Image Length: 384 Image Depth: 1<br>
  Tile Width: 128 Tile Length: 128 Tile Depth: 1<br>
  Bits/Sample: 8<br>
  Sample Format: void<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 128<br>
  Min Sample Value: 0<br>
  Max Sample Value: 255<br>
  Planar Configuration: single image plane<br>
<br>
</code></pre>
<h3>b05937c07e0f3ce1bfd2c8c71b0220ec.tif</h3>

<ul><li>Origin: <code>http://www.haui.edu.vn/tailieu/duhoc/toana2.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x981d2 (623058)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1205 Image Length: 1719<br>
  Tile Width: 1216 Tile Length: 1728<br>
  Resolution: 150, 150 pixels/inch<br>
  Position: 0, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 2<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 633154<br>
  Model: EPSON Perfection 2480/2580<br>
  Software: Microsoft Office Document Scanning  1.03.2349.01 <br>
  DateTime: 2007:09:10 15:14:12<br>
  Artist: QTKD<br>
  JpegInterchangeFormat: 8<br>
  JpegInterchangeFormatLength: 617390<br>
  JpegProc: 1<br>
TIFF Directory at offset 0x117ffa (1146874)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1112 Image Length: 1664<br>
  Tile Width: 1120 Tile Length: 1664<br>
  Resolution: 150, 150 pixels/inch<br>
  Position: 0, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: min-is-black<br>
  YCbCr Subsampling: 2, 2<br>
  Samples/Pixel: 1<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 1155912<br>
  Model: EPSON Perfection 2480/2580<br>
  Software: Microsoft Office Document Scanning  1.03.2349.01 <br>
  DateTime: 2007:09:10 15:15:06<br>
  Artist: QTKD<br>
  JpegInterchangeFormat: 633316<br>
  JpegInterchangeFormatLength: 511934<br>
  JpegProc: 1<br>
TIFF Directory at offset 0x123328 (1192744)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2130 Image Length: 3341<br>
  Resolution: 300, 300 pixels/inch<br>
  Position: 0, 0<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 240<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 1200156<br>
  Model: EPSON Perfection 2480/2580<br>
  Software: Microsoft Office Document Scanning  1.03.2349.01 <br>
  DateTime: 2007:09:10 15:15:48<br>
  Artist: QTKD<br>
<br>
</code></pre>
<h3>m1-b0d36ed02fc2624ac79d3144e8b1bda2.tif</h3>

<h3>m2-b0d36ed02fc2624ac79d3144e8b1bda2.tif</h3>

<h3>m3-b0d36ed02fc2624ac79d3144e8b1bda2.tif</h3>

<ul><li>Origin: <code>http://www.gsfc.nasa.gov/gsfc/spacesci/pictures/20020509imagessu/mag3.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-b0d36ed02fc2624ac79d3144e8b1bda2.tif:<br>
TIFF Directory at offset 0x767fe (485374)<br>
  Image Width: 1024 Image Length: 768<br>
  Resolution: 1, 0.99975 (unitless)<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 4<br>
  Planar Configuration: single image plane<br>
  ImageDescription: Composer: Untitled, frame 0<br>
  Software: Co�poser<br>
  DateTime: Tue May  7 21:48:30 2002<br>
  Artist: maya<br>
  HostComputer: thor<br>
m2-b0d36ed02fc2624ac79d3144e8b1bda2.tif:<br>
TIFF Directory at offset 0x767fe (485374)<br>
  Image Width: 1024 Image Length: 768<br>
  Resolution: 2, 0 (unitless)<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Samples/Pixel: 4<br>
  Planar Configuration: single image plane<br>
  Transfer Function: (present)<br>
  Software: Composer<br>
  DateTime: Tue May  7 21:48:30 2002<br>
  Artist: maya<br>
  HostComputer: thor<br>
m3-b0d36ed02fc2624ac79d3144e8b1bda2.tif:<br>
<br>
</code></pre>
<h3>b1247c37897d354610a07ddfe17eb669.tif</h3>

<ul><li>Origin: <code>http://elyon1.court.gov.il/heb/tovanot_yezugiyot/154.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x98d4 (39124)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2311<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2311<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:39:13<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x13e52 (81490)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:39:33<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x1ebd8 (125912)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2307<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2307<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:39:54<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x29844 (170052)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 3-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:40:15<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x34908 (215304)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2307<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2307<br>
  Planar Configuration: single image plane<br>
  Page Number: 4-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:40:36<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x3fdaa (261546)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 5-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:40:58<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x455a8 (284072)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2306<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2306<br>
  Planar Configuration: single image plane<br>
  Page Number: 6-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:41:10<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x4e568 (320872)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 7-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:41:28<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x591f0 (365040)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2306<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2306<br>
  Planar Configuration: single image plane<br>
  Page Number: 8-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:41:49<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x62f3a (405306)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2425<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2425<br>
  Planar Configuration: single image plane<br>
  Page Number: 9-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:42:08<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 10<br>
  Consecutive Bad Fax Lines: 8<br>
TIFF Directory at offset 0x6d612 (448018)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 10-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:42:28<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x77e48 (491080)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2306<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2306<br>
  Planar Configuration: single image plane<br>
  Page Number: 11-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:42:48<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x7d0ce (512206)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 12-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:43:00<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x8747e (554110)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2306<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2306<br>
  Planar Configuration: single image plane<br>
  Page Number: 13-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:43:20<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x8bc82 (572546)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 14-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:43:31<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0x9d140 (643392)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2307<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2307<br>
  Planar Configuration: single image plane<br>
  Page Number: 15-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:44:04<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0xa3fd0 (671696)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 16-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:44:19<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0xa9cb2 (695474)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2307<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2307<br>
  Planar Configuration: single image plane<br>
  Page Number: 17-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:44:31<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0xb0616 (722454)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2305<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2305<br>
  Planar Configuration: single image plane<br>
  Page Number: 18-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:44:45<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 5<br>
  Consecutive Bad Fax Lines: 3<br>
TIFF Directory at offset 0xbad04 (765188)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2306<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2306<br>
  Planar Configuration: single image plane<br>
  Page Number: 19-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:45:05<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0xc5da2 (810402)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 20-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:45:26<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0xd3554 (865620)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2308<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2308<br>
  Planar Configuration: single image plane<br>
  Page Number: 21-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:45:51<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0xe1fb2 (925618)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2310<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2310<br>
  Planar Configuration: single image plane<br>
  Page Number: 22-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:46:19<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
TIFF Directory at offset 0xe5c50 (941136)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 2305<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2305<br>
  Planar Configuration: single image plane<br>
  Page Number: 23-0<br>
  ImageDescription: <br>
  Software: Dialogic - Cheetah Dm3Fax version 1.00<br>
  DateTime: 2008:02:13 14:46:28<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: receiver regenerated (1 = 0x1)<br>
  Bad Fax Lines: 2<br>
  Consecutive Bad Fax Lines: 2<br>
<br>
</code></pre>
<h3>m1-b127f0fb89daedea07abb50b9db2dfd9.tif</h3>

<ul><li>Origin: <code>http://lexicon.ff.cuni.cz/tiff/pgmc_torp/b0045.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>m1-b1ab6f4b81e9b8020a90c8f2c9bcfedb.tif</h3>

<h3>m2-b1ab6f4b81e9b8020a90c8f2c9bcfedb.tif</h3>

<ul><li>Origin: <code>http://mvhwrestle.net/pipermail/wrestlers_mvhwrestle.net/attachments/20080302/657a88ee/attachment-0001.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-b1ab6f4b81e9b8020a90c8f2c9bcfedb.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1728 Image Length: 1078<br>
  Resolution: 204, 0 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1078<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-0<br>
  ImageDescription:         15102780734                 K7FAX  Thu Feb 28 09:42:34 2008<br>
<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: (140 = 0x8c)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
m2-b1ab6f4b81e9b8020a90c8f2c9bcfedb.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1728 Image Length: 1078<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1078<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-0<br>
  ImageDescription:          151_2770734             e   K7FAX  Thu Feb 28 09:42:34 2008<br>
<br>
  Group 3 Options: (0 = 0x0)<br>
  Fax Data: clean (0 = 0x0)<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0xef0b (61195)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1728 Image Length: 1077<br>
  Resolution: 64, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1077<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-0<br>
  ImageDescription:          15102780734                 K7FAX  Thu Feb 28 09:43:12 2008<br>
<br>
  Group 3 Options: (0 = 0x0)<br>
  Bad Fax Lines: 0<br>
  Consecutive Bad Fax Lines: 0<br>
<br>
</code></pre>
<h3>b52a2fceb34f9b31cb417379cf8c02ba.tif</h3>

<ul><li>Origin: <code>http://www.brixen.tirol.gv.at/gelbeseite/logo/50074821.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x18ea (6378)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 54 Image Length: 50<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  YCbCr Positioning: 0 (0x0)<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 50<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-0<br>
  Software: Adobe Photoshop CS Macintosh<br>
  DateTime: 2006:01:05 12:54:59<br>
  White Point: 0-0<br>
  PrimaryChromaticities: 0.000000,0.000000,0.000000,0.000000,0.000000,0.000000<br>
  YCbCrCoefficients: 0.000000,0.000000,0.000000<br>
  Reference Black/White:<br>
     0:     0     0<br>
     1:     0     0<br>
     2:     0     0<br>
  XMLPacket (XMP Metadata): Present<br>
  EXIFIFDOffset: 0x142<br>
  Predictor: horizontal differencing 2 (0x2)<br>
<br>
</code></pre>
<h3>b9bc00e0fb28f2a525c0acfe78251eda.tif</h3>

<ul><li>Origin: <code>http://vas.lex.bg/files/faxview.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8b6c (35692)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1163<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1163<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-0<br>
  Software: Windows NT Fax Server<br>
  Fax Data: clean (0 = 0x0)<br>
  Consecutive Bad Fax Lines: 0<br>
TIFF Directory at offset 0xc1fa (49658)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1728 Image Length: 1169<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: lsb-to-msb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 1169<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-0<br>
  Software: Windows NT Fax Server<br>
  Fax Data: clean (0 = 0x0)<br>
  Consecutive Bad Fax Lines: 0<br>
<br>
</code></pre>
<h3>m1-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif</h3>

<h3>m2-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif</h3>

<h3>m3-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif</h3>

<h3>m4-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif</h3>

<h3>m5-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif</h3>

<h3>m6-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif</h3>

<ul><li>Origin: <code>http://www.mof.go.th/rule/picture/590_doc.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif:<br>
TIFF Directory at offset 0x48 (72)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1950 Image Length: 2454<br>
  Resolution: 300, 0 pixels/inch<br>
  Bits/Sample: 26<br>
  Compression Scheme: CCITT RLE<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Planar Configuration: single image plane<br>
TIFF Directory at offset 0xba84 (47748)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 966 Image Length: 1497<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 38176<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
m2-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif:<br>
TIFF Directory at offset 0x48 (72)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1950 Image Length: 2454<br>
  Resolution: 300, 0 pixels/inch<br>
  Bits/Sample: 26<br>
  Compression Scheme: CCITT RLE<br>
  Photometric Interpretation: min-is-white<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 130<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
m3-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif:<br>
TIFF Directory at offset 0x48 (72)<br>
  Image Width: 1950 Image Length: 2454<br>
  Resolution: 300, 0<br>
  Bits/Sample: 26<br>
  Compression Scheme: CCITT RLE<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Planar Configuration: single image plane<br>
TIFF Directory at offset 0xba84 (47748)<br>
  Image Width: 966 Image Length: 1497<br>
  Resolution: 1.04084, 150 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 32<br>
  Planar Configuration: single image plane<br>
  Ink Set: CMYK<br>
  Software: Oi/GFS� writer v00.06.01P&amp;<br>
m4-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif:<br>
TIFF Directory at offset 0x48 (72)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1950 Image Length: 2454<br>
  Resolution: 300, 0 pixels/inch<br>
  Bits/Sample: 26<br>
  Compression Scheme: CCITT RLE<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 130<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
TIFF Directory at offset 0xba84 (47748)<br>
  Image Width: 966 Image Length: 1497<br>
  Resolution: 150, 150 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 32<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
m5-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif:<br>
TIFF Directory at offset 0x48 (72)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1950 Image Length: 2454<br>
  Bits/Sample: 26<br>
  Compression Scheme: CCITT RLE<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 130<br>
  SMax Sample Value: 300<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
m6-bfa1e2fb1d67bcd9d902a0dbf5badb70.tif:<br>
TIFF Directory at offset 0x48 (72)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1950 Image Length: 2454<br>
  Resolution: 300, 0 pixels/inch<br>
  Bits/Sample: 26<br>
  Compression Scheme: CCITT RLE<br>
  Photometric Interpretation: min-is-white<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 130<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.01P<br>
<br>
</code></pre>
<h3>c0d253443d8d4241035fff993ea0581b.tif</h3>

<ul><li>Origin: <code>http://www.runwaymiami.com/wp-content/uploads/2008/07/tibi.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 600 Image Length: 1400<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 1, 1<br>
  YCbCr Positioning: cosited<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 36<br>
  Planar Configuration: single image plane<br>
  Make: Canon<br>
  Model: Canon EOS 5D<br>
  Software: Adobe Photoshop 7.0<br>
  DateTime: 2008:07:16 16:27:13<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 4142 bytes<br>
  EXIFIFDOffset: 0x41eec<br>
  ICC Profile: &lt;present&gt;, 3144 bytes<br>
  JPEG Tables: (558 bytes)<br>
TIFF Directory at offset 0x41eec (270060)<br>
  ExposureTime: 0.010000<br>
  FNumber: 13.000000<br>
  ExposureProgram: 1<br>
  ISOSpeedRatings: 400<br>
  ExifVersion: 0x30,0x32,0x32,0x31<br>
  DateTimeOriginal: 2008:07:14 23:12:10<br>
  DateTimeDigitized: 2008:07:14 23:12:10<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  ShutterSpeedValue: 6.625000<br>
  ApertureValue: 7.375000<br>
  ExposureBiasValue: 0.000000<br>
  MeteringMode: 5<br>
  Flash: 16<br>
  FocalLength: 38.000000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 1<br>
  PixelXDimension: 600<br>
  PixelYDimension: 1400<br>
  FocalPlaneXResolution: 3086.925781<br>
  FocalPlaneYResolution: 3091.295166<br>
  FocalPlaneResolutionUnit: 2<br>
  CustomRendered: 0<br>
  ExposureMode: 1<br>
  WhiteBalance: 0<br>
  SceneCaptureType: 0<br>
<br>
</code></pre>
<h3>c16f4894de3142b98e8f3d8fc6b3d23e.tif</h3>

<ul><li>Origin: <code>http://img1.xooimage.com/files/c/1/6/a-lire-a38a7a.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x7562 (30050)<br>
  Image Width: 50 Image Length: 50<br>
  Resolution: 1000, 1000 pixels/inch<br>
  Bits/Sample: 32<br>
  Sample Format: IEEE floating point<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 218<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop CS4 Macintosh<br>
  DateTime: 2009:01:18 18:41:23<br>
  EXIFIFDOffset: 0x8<br>
  ICC Profile: &lt;present&gt;, 600 bytes<br>
TIFF Directory at offset 0x8 (8)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 50<br>
  PixelYDimension: 50<br>
<br>
</code></pre>
<h3>ccd82bb72407d0ca03cac50eb42faf47.tif</h3>

<ul><li>Origin: <code>http://www.lizparrypr.co.uk/wp-content/uploads/2008/08/new-adobe-photoshop-image.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 347 Image Length: 80<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 80<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop CS Windows<br>
  DateTime: 2008:08:06 15:31:22<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 3850 bytes<br>
  EXIFIFDOffset: 0x42b0<br>
  ICC Profile: &lt;present&gt;, 3144 bytes<br>
  JPEG Tables: (459 bytes)<br>
TIFF Directory at offset 0x42b0 (17072)<br>
  ColorSpace: 1<br>
  PixelXDimension: 347<br>
  PixelYDimension: 80<br>
<br>
</code></pre>
<h3>ce50e53224a3b62bb821bc294bf6a588.tif</h3>

<ul><li>Origin: <code>http://xce.xanga.com/50e8516b463a8230354080/b181528215.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x5c6fe (378622)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 564 Image Length: 423<br>
  Resolution: 96, 96 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  YCbCr Positioning: cosited<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 7<br>
  Planar Configuration: single image plane<br>
  ImageDescription: OLYMPUS DIGITAL CAMERA         <br>
  Make: OLYMPUS IMAGING CORP.<br>
  Model: FE190/X750<br>
  Software: Version 1.0<br>
  DateTime: 2009:01:19 22:56:26<br>
  Predictor: none 1 (0x1)<br>
<br>
</code></pre>
<h3>m1-d0f86ab189cbe900ec389ca6d7464713.tif</h3>

<h3>m2-d0f86ab189cbe900ec389ca6d7464713.tif</h3>

<h3>m3-d0f86ab189cbe900ec389ca6d7464713.tif</h3>

<h3>m4-d0f86ab189cbe900ec389ca6d7464713.tif</h3>

<h3>m5-d0f86ab189cbe900ec389ca6d7464713.tif</h3>

<ul><li>Origin: <code>http://www.earsandeyes.com/downloads/logo_eae.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-d0f86ab189cbe900ec389ca6d7464713.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2717 Image Length: 385<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 96<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop CS2 Macintosh<br>
  DateTime: 2007:12:02 14:43:35<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 11226 bytes<br>
  EXIFIFDOffset: 0xb5300<br>
  ICC Profile: &lt;present&gt;, 557168 bytes<br>
  JPEG Tables: (285 bytes)<br>
TIFF Directory at offset 0xb5300 (742144)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 2717<br>
  PixelYDimension: 385<br>
m2-d0f86ab189cbe900ec389ca6d7464713.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Image Width: 1949 Image Length: 385<br>
  Resolution: inf, 0 pixels/inch<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 34564<br>
  Rows/Strip: 96<br>
  Planar Configuration: single image plane<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 11226 bytes<br>
  EXIFIFDOffset: 0xb5300<br>
  ICC Profile: &lt;present&gt;, 557168 bytes<br>
m3-d0f86ab189cbe900ec389ca6d7464713.tif:<br>
m4-d0f86ab189cbe900ec389ca6d7464713.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2717 Image Length: 385<br>
  Resolution: 300, 0 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: separated<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 96<br>
  Planar Configuration: single image plane<br>
  Software: Adobe Photoshop CS2 Macintosh<br>
  DateTime: 2007:12:02 14:43:35<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 11226 bytes<br>
  EXIFIFDOffset: 0xb5300<br>
  ICC Profile: &lt;present&gt;, 557168 bytes<br>
TIFF Directory at offset 0xb5300 (742144)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 2717<br>
  PixelYDimension: 385<br>
m5-d0f86ab189cbe900ec389ca6d7464713.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Image Width: 2717 Image Length: 1<br>
  Resolution: 300, 300 pixels/inch<br>
  Compression Scheme: JPEG<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 96<br>
  Planar Configuration: single image plane<br>
  HostComputer: <br>
  Software: Adobe Photoshop CS2 Macintosh<br>
  DateTime: 2007:12:02 14:43:35<br>
  EXIFIFDOffset: 0xb5300<br>
  ICC Profile: &lt;present&gt;, 557168 bytes<br>
  JPEG Tables: (285 bytes)<br>
TIFF Directory at offset 0xb5300 (742144)<br>
  ColorSpace: 65535<br>
  PixelXDimension: 4262557<br>
  PixelYDimension: 385<br>
<br>
</code></pre>
<h3>m1-d1d366d7965db766c19a66c7a2ccbb6b.tif</h3>

<h3>m2-d1d366d7965db766c19a66c7a2ccbb6b.tif</h3>

<h3>m3-d1d366d7965db766c19a66c7a2ccbb6b.tif</h3>

<h3>m4-d1d366d7965db766c19a66c7a2ccbb6b.tif</h3>

<h3>m5-d1d366d7965db766c19a66c7a2ccbb6b.tif</h3>

<h3>m6-d1d366d7965db766c19a66c7a2ccbb6b.tif</h3>

<ul><li>Origin: <code>http://www.ilgridodeipoveri.org/gdp/images/img_11312.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-d1d366d7965db766c19a66c7a2ccbb6b.tif:<br>
m2-d1d366d7965db766c19a66c7a2ccbb6b.tif:<br>
TIFF Directory at offset 0x2bbe2 (179170)<br>
  Image Width: 324 Image Length: 450<br>
  Bits/Sample: 8<br>
  Sample Format: unsigned integer<br>
  Compression Scheme: LZW<br>
  Extra Samples: 1&lt;assoc-alpha&gt;<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 37477<br>
  Planar Configuration: single image plane<br>
  Software: M	c OS X 10.4.11 (8S165)<br>
  DateTime: 2008:06:17 10:03:36<br>
  Artist: M�tteo Della Torrg<br>
  ICC Profile: &lt;present&gt;, 3176 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
m3-d1d366d7965db766c19a66c7a2ccbb6b.tif:<br>
m4-d1d366d7965db766c19a66c7a2ccbb6b.tif:<br>
m5-d1d366d7965db766c19a66c7a2ccbb6b.tif:<br>
m6-d1d366d7965db766c19a66c7a2ccbb6b.tif:<br>
<br>
</code></pre>
<h3>d274ea7f91216b3f5125acb4c138870e.tif</h3>

<ul><li>Origin: <code>http://www.cfav.co.uk/misc/projector/sch_f56_imi_g15_blhq_rev.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x75bca0 (7716000)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1388 Image Length: 1036<br>
  Resolution: 0, 0<br>
  Bits/Sample: 16<br>
  Sample Format: void<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Halftone Hints: light 0 dark 0<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 1<br>
  Min Sample Value: 0<br>
  Max Sample Value: 65535<br>
  Planar Configuration: single image plane<br>
  Software: ActivR<br>
<br>
</code></pre>
<h3>d664a73588796b59191ad8628065f04a.tif</h3>

<ul><li>Origin: <code>http://www.nag.ru/goodies/certificates/other/licence8.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x400 (1024)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 4956 Image Length: 7014<br>
  Resolution: 600, 600 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 51<br>
  Planar Configuration: single image plane<br>
  Software: Oi/GFS, writer v00.06.00P, (c) Wang Labs, Inc. 1990, 1991<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x8 (8)<br>
  Image Width: 1239 Image Length: 1754<br>
  Resolution: 150, 150<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 2, 2<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 1754<br>
  Planar Configuration: single image plane<br>
  JpegInterchangeFormat: 232<br>
  JpegInterchangeFormatLength: 623<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x358 (856)<br>
  Subfile Type: reduced-resolution image (1 = 0x1)<br>
  Image Width: 64 Image Length: 90<br>
  Resolution: 8, 8<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 90<br>
  Planar Configuration: single image plane<br>
<br>
</code></pre>
<h3>e00804b3169008f1c00bf250edccdae4.tif</h3>

<ul><li>Origin: <code>http://www.nhinb.gov.tw/upfiles/adupload/dwn1285509594.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x1374a (79690)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1664 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: min-is-black<br>
  Thresholding: bilevel art scan<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 59<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-3<br>
  Make: RICOH<br>
  Predictor: none 1 (0x1)<br>
TIFF Directory at offset 0x1de2e (122414)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1664 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-3<br>
  Make: RICOH<br>
TIFF Directory at offset 0x20e9e (134814)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1664 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-3<br>
  Make: RICOH<br>
<br>
</code></pre>
<h3>m1-e07fcd0e2ea8a9f41c6baed2f651bb8d.tif</h3>

<ul><li>Origin: <code>http://jnul.huji.ac.il/dl/newspapers/hazefirah/index/25-1898/index2501.tif</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>e45931b568d12c9905b1db1775321972.tif</h3>

<ul><li>Origin: <code>http://www.livingsteel.org/media/shortlist2007/hideto_horike_uk02.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2362 Image Length: 1574<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 1574<br>
  Planar Configuration: single image plane<br>
  Make: Canon<br>
  Model: Canon EOS D30<br>
  Software: Adobe Photoshop CS2 Windows<br>
  DateTime: 2007:06:13 13:42:54<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 5698 bytes<br>
  EXIFIFDOffset: 0xaa95a4<br>
  ICC Profile: &lt;present&gt;, 3144 bytes<br>
TIFF Directory at offset 0xaa95a4 (11179428)<br>
  ExposureTime: 3.000000<br>
  FNumber: 22.000000<br>
  ISOSpeedRatings: 100<br>
  ExifVersion: 0x30,0x32,0x31,0x30<br>
  DateTimeOriginal: 2007:05:10 00:50:33<br>
  DateTimeDigitized: 2007:05:10 00:50:33<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  CompressedBitsPerPixel: 3.000000<br>
  ShutterSpeedValue: -1.584946<br>
  ApertureValue: 8.918869<br>
  ExposureBiasValue: 0.000000<br>
  MaxApertureValue: 4.000000<br>
  SubjectDistance: 0.000000<br>
  MeteringMode: 5<br>
  Flash: 0<br>
  FocalLength: 30.000000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 1<br>
  PixelXDimension: 2362<br>
  PixelYDimension: 1574<br>
  FocalPlaneXResolution: 2421.524658<br>
  FocalPlaneYResolution: 2420.167969<br>
  FocalPlaneResolutionUnit: 2<br>
  SensingMethod: 2<br>
<br>
</code></pre>
<h3>ebad222e9402d00e371c92ab5da86e6b.tif</h3>

<ul><li>Origin: <code>http://www.martinsound.com/images/p3_mmu24.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 900 Image Length: 699<br>
  Resolution: 220, 220 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: separated<br>
  Samples/Pixel: 4<br>
  Rows/Strip: 2<br>
  Planar Configuration: single image plane<br>
  Make: Canon<br>
  Model: Canon PowerShot S20<br>
  Software: Adobe Photoshop 7.0<br>
  DateTime: 2002:07:24 12:44:15<br>
  Dot Range: 0-255<br>
  XMLPacket (XMP Metadata): Present<br>
  Photoshop Data: &lt;present&gt;, 13850 bytes<br>
  EXIFIFDOffset: 0x18d6e0<br>
  ICC Profile: &lt;present&gt;, 557168 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x18d6e0 (1627872)<br>
  ExposureTime: 0.005556<br>
  FNumber: 5.600000<br>
  ExifVersion: 0x30,0x32,0x31,0x30<br>
  DateTimeOriginal: 2001:08:10 14:08:24<br>
  DateTimeDigitized: 2001:08:10 14:08:24<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  CompressedBitsPerPixel: 6.000000<br>
  ShutterSpeedValue: 7.491852<br>
  ApertureValue: 4.970856<br>
  ExposureBiasValue: 0.000000<br>
  MaxApertureValue: 2.900000<br>
  SubjectDistance: 0.727000<br>
  MeteringMode: 2<br>
  Flash: 0<br>
  FocalLength: 13.000000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 65535<br>
  PixelXDimension: 900<br>
  PixelYDimension: 699<br>
  FocalPlaneXResolution: 7366.906250<br>
  FocalPlaneYResolution: 7349.282227<br>
  FocalPlaneResolutionUnit: 2<br>
  SensingMethod: 2<br>
<br>
</code></pre>
<h3>ecf22eaecaf11fc75938973745138868.tif</h3>

<ul><li>Origin: <code>http://memory.loc.gov/pnp/habshaer/ca/ca1600/ca1604/data/002.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1696 Image Length: 2200<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: 64 (0x40)<br>
  FillOrder: msb-to-lsb<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2200<br>
  Planar Configuration: single image plane<br>
  DocumentName: /habshaer/ca/ca1600/ca1604/data/002.tif<br>
  Software: Systems Integration Group,Inc,17:40:52<br>
  DateTime: 1997:08:25:13:12:50<br>
  Artist: Library of Congress<br>
<br>
</code></pre>
<h3>m1-ed254aa9f390aab319728b42e00a73e7.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Image Width: 1512 Image Length: 359<br>
  Resolution: 296.64, 296.64<br>
  Bits/Sample: 4<br>
  Compression Scheme: ThunderScan<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 64<br>
  Planar Configuration: single image plane<br>
TIFF Directory at offset 0x1514c (86348)<br>
  Image Width: 1512 Image Length: 359<br>
  Resolution: 0, 296.64<br>
  Bits/Sample: 1<br>
  Compression Scheme: None<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 64<br>
  Planar Configuration: single image plane<br>
<br>
</code></pre>
<h3>efb780f70a7d94fa98adfc98d2aa8d50.tif</h3>

<ul><li>Origin: <code>http://www.mobiset.ru/photos/2008/september/02/motorola_zn5/raw2.tiff</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2624 Image Length: 1948<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: min-is-black<br>
  Orientation: row 0 top, col 0 lhs<br>
  Rows/Strip: 1948<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 11592<br>
  Make: MOTOROLA INC<br>
  Model: PIXL<br>
  EXIFIFDOffset: 0x23c<br>
  Software: R6637_G_81.00.47I_TOR<br>
TIFF Directory at offset 0x23c (572)<br>
  ExposureTime: 0.001502<br>
  FNumber: 5.600000<br>
  ExposureProgram: 2<br>
  ISOSpeedRatings: 62<br>
  ExifVersion: 0x30,0x31,0x31,0x30<br>
  ShutterSpeedValue: 6.000000<br>
  SubjectDistance: inf<br>
  MeteringMode: 0<br>
  LightSource: 0<br>
  Flash: 0<br>
  FocalLength: 5.800000<br>
  MakerNote: ...<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  SensingMethod: 2<br>
<br>
</code></pre>
<h3>m1-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m2-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m3-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m4-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m5-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m6-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m7-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m8-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<h3>m9-f0d7bcb90496c323c880a9773dfe93ff.tif</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
TIFF Directory at offset 0x5b6e (23406)<br>
  Image Width: 512 Image Length: 384<br>
  Position: 0, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 16<br>
  Planar Configuration: single image plane<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JPEG Tables: (574 bytes)<br>
m2-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
TIFF Directory at offset 0x5b6e (23406)<br>
  Image Width: 512 Image Length: 384<br>
  Position: 0, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 16<br>
  Planar Configuration: single image plane<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JPEG Tables: (574 bytes)<br>
m3-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
TIFF Directory at offset 0x5b6e (23406)<br>
  Image Width: 512 Image Length: 384<br>
  Position: 0, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 16<br>
  Planar Configuration: single image plane<br>
  JPEG Tables: (574 bytes)<br>
m4-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
m5-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
TIFF Directory at offset 0x5b6e (23406)<br>
  Image Width: 512 Image Length: 384<br>
  Resolution: 16, 0<br>
  Position: 0, 1.32383e+07<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1: 124.786   255<br>
     2:   128   255<br>
  JPEG Tables: (574 bytes)<br>
m6-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
TIFF Directory at offset 0x5b6e (23406)<br>
  Image Width: 512 Image Length: 384<br>
  Position: 0, 738.702<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Planar Configuration: single image plane<br>
  Reference Black/White:<br>
     0:     0   255<br>
     1: 124.786   255<br>
     2:   128   255<br>
  JPEG Tables: (574 bytes)<br>
m7-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
TIFF Directory at offset 0x5b6e (23406)<br>
  Image Width: 512 Image Length: 384<br>
  Position: 0, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 16<br>
  Planar Configuration: single image plane<br>
  HostComputer: <br>
  Reference Black/White:<br>
     0:     0   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JPEG Tables: (574 bytes)<br>
m8-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
TIFF Directory at offset 0x5b6e (23406)<br>
  Image Width: 20224 Image Length: 384<br>
  Position: 40192, 0<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 16<br>
  Planar Configuration: single image plane<br>
  Reference Black/White:<br>
     0: 9.96147e+06   255<br>
     1:   128   255<br>
     2:   128   255<br>
  JPEG Tables: (574 bytes)<br>
m9-f0d7bcb90496c323c880a9773dfe93ff.tif:<br>
<br>
</code></pre>
<h3>f15fca5bfdef640840d8ea30570c8cea.tif</h3>

<ul><li>Origin: <code>http://www.oktoberpromotion.com/files/media/pascalfinkenauer3new-fotosvensindt.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 995 Image Length: 1181<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 87<br>
  Planar Configuration: single image plane<br>
  SubIFD Offsets: 1347048<br>
  Software: Adobe Photoshop CS3 Macintosh<br>
  DateTime: 2008:11:13 18:29:11<br>
  XMLPacket (XMP Metadata): Present<br>
  RichTIFFIPTC Data: &lt;present&gt;, 8 bytes<br>
  Photoshop Data: &lt;present&gt;, 12804 bytes<br>
  EXIFIFDOffset: 0x148db0<br>
  ICC Profile: &lt;present&gt;, 4376 bytes<br>
  Predictor: horizontal differencing 2 (0x2)<br>
TIFF Directory at offset 0x148db0 (1346992)<br>
  ExifVersion: 0x30,0x32,0x32,0x30<br>
  ColorSpace: 65535<br>
  PixelXDimension: 995<br>
  PixelYDimension: 1181<br>
<br>
</code></pre>
<h3>m1-f228b1103fd7b629c08c1bbba94708e0.tif</h3>

<h3>m2-f228b1103fd7b629c08c1bbba94708e0.tif</h3>

<ul><li>Origin: <code>http://das.ntl.gov.tw/xdcm/xml/show_img.jsp?file_name=cca100003-nw-tmsjp19480318-02-i.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-f228b1103fd7b629c08c1bbba94708e0.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 4680 Image Length: 6400<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 6400<br>
  Planar Configuration: single image plane<br>
  ImageDescription: Adobe Photoshop 7.0<br>
  Make: techsoft as - P.O.BOX 132, N-3201 Sandefjord,NORWAY<br>
  Software: PixEdit Version 6.2.2.0, SN 246-50188-02,  used by Owner at Your Company Name<br>
  DateTime: 2008:01:05 13:29:0<br>
  EXIFIFDOffset: 0x1d0<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x1d0 (464)<br>
  ColorSpace: 65535<br>
m2-f228b1103fd7b629c08c1bbba94708e0.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 4680 Image Length: 6400<br>
  Resolution: 300, 300 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  FillOrder: msb-to-lsb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 6400<br>
  Planar Configuration: single image plane<br>
  ImageDescription: Adobe Photoshop 7.0<br>
  Make: techsoft as - P.O.BOX 132, N-3201 Sandefjord,NORWAY<br>
  Software: PixEdit Version 6.2.2.0, SN 246-50188-02,  used by Owner at Your Company Name<br>
  DateTime: 2008:01:05 13:29:0<br>
  EXIFIFDOffset: 0x1d0<br>
  Group 4 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x1d0 (464)<br>
  ColorSpace: 65535<br>
<br>
</code></pre>
<h3>m1-f4830e8d4fa458f78a09fcaaf260569c.tif</h3>

<h3>m2-f4830e8d4fa458f78a09fcaaf260569c.tif</h3>

<ul><li>Origin: <code>http://www.abbasministries.org/press_release/images/abbas_high_res.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-f4830e8d4fa458f78a09fcaaf260569c.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2085 Image Length: 1536<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 1, 1<br>
  YCbCr Positioning: cosited<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 167<br>
  Planar Configuration: single image plane<br>
  Make: FUJIFILM<br>
  Model: FinePixS2Pro<br>
  Software: Adobe Photos:op CS2 Windows<br>
  XMLPacket (XMP Metadata): Present<br>
  Copyright:     <br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 7112 bytes<br>
  EXIFIFDOffset: 0x839c8<br>
  JPEG Tables: (558 bytes)<br>
TIFF Directory at offset 0x839c8 (539080)<br>
  ExposureTime: 0.016667<br>
  ExposureProgram: 1<br>
  ISOSpeedRatings: 1600<br>
  ExifVersion: 0x30,0x32,0x32,0x30<br>
  DateTimeOriginal: 2005:03:03 15:31:45<br>
  DateTimeDigitized: 2005:03:03 15:31:45<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  CompressedBitsPerPixel: 3.200000<br>
  ShutterSpeedValue: 0.000043<br>
  ApertureValue: 4.500000<br>
  BrightnessValue: 1.000000<br>
  ExposureBiasValue: 0.000000<br>
  MeteringMode: 3<br>
  LightSource: 0<br>
  Flash: 9<br>
  FocalLength: 34.000000<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 65535<br>
  PixelXDimension: 2085<br>
  PixelYDimension: 1536<br>
  FocalPlaneXResolution: 1007.000000<br>
  FocalPlaneYResolution: 1007.000000<br>
  FocalPlaneResolutionUnit: 3<br>
  SensingMethod: 2<br>
  CustomRendered: 0<br>
  ExposureMode: 1<br>
  WhiteBalance: 0<br>
  FocalLengthIn35mmFilm: 51<br>
  SceneCaptureType: 0<br>
  Contrast: 2<br>
  Saturation: 0<br>
  Sharpness: 2<br>
  SubjectDistanceRange: 0<br>
m2-f4830e8d4fa458f78a09fcaaf260569c.tif:<br>
TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 2085 Image Length: 1536<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 1, 1<br>
  YCbCr Positioning: cosited<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 167<br>
  Planar Configuration: single image plane<br>
  Make: FUJIFILM<br>
  Model: FinePixS2Pro<br>
  Software: Adobe Photoshop CS2 Windows<br>
  DateTime: 2006:11:16 22:13:39<br>
  XMLPacket (XMP Metadata): Present<br>
  Copyright:    �<br>
  RichTIFFIPTC Data: &lt;present&gt;, 16 bytes<br>
  Photoshop Data: &lt;present&gt;, 7112 bytes<br>
  EXIFIFDOffset: 0x839c8<br>
  JPEG Tables: (558 bytes)<br>
TIFF Directory at offset 0x839c8 (539080)<br>
  ExposureTime: 0.016667<br>
  FNumber: 4.800000<br>
  ExposureProgram: 1<br>
  ISOSpeedRatings: 1600<br>
  ExifVersion: 0x30,0x32,0x32,0x30<br>
  DateTimeOriginal: 2005:0�:03 15:31:45<br>
  DateTimeDigitized: 2005:03:03 15:31:45<br>
  ComponentsConfiguration: 0x1,0x2,0x3,0x0<br>
  CompressedBitsPerPixel: 3.200000<br>
  ShutterSpeedValue: 6.000000<br>
  ApertureValue: 4.500000<br>
  BrightnessValue: 1.000000<br>
  LightSource: 0<br>
  Flash: 9<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 65535<br>
  PixelXDimension: 2085<br>
  PixelYDimension: 1536<br>
  FocalPlaneYResolution: 1007.000000<br>
  FocalPlaneResolutionUnit: 3<br>
  SensingMethod: 2<br>
  CustomRendered: 0<br>
  ExposureMode: 1<br>
  WhiteBalance: 0<br>
  FocalLengthIn35mmFilm: 51<br>
  SceneCaptureType: 0<br>
  Contrast: 2<br>
  Sharpness: 2<br>
  SubjectDistanceRange: 0<br>
<br>
</code></pre>
<h3>f4bcc246f3471102a2dea2ee9153b372.tif</h3>

<ul><li>Origin: <code>http://www.snowbound.com/images/circledot.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1336 Image Length: 548<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 2<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 548<br>
  Planar Configuration: single image plane<br>
  DateTime: 06:01:1998<br>
  Artist: Copyright Snowbound Software 1998<br>
  JpegInterchangeFormat: 504<br>
TIFF Directory at offset 0x1150b (70923)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1336 Image Length: 548<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 2<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 548<br>
  Planar Configuration: single image plane<br>
  DateTime: 06:01:1998<br>
  Artist: Copyright Snowbound Software 1998<br>
  JpegInterchangeFormat: 71419<br>
TIFF Directory at offset 0x19fbf (106431)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1336 Image Length: 548<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 2<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 548<br>
  Planar Configuration: single image plane<br>
  DateTime: 06:01:1998<br>
  Artist: Copyright Snowbound Software 1998<br>
  JpegInterchangeFormat: 106927<br>
TIFF Directory at offset 0x2b97b (178555)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1336 Image Length: 548<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  FillOrder: msb-to-lsb<br>
  YCbCr Subsampling: 2, 2<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 548<br>
  Planar Configuration: single image plane<br>
  DateTime: 06:01:1998<br>
  Artist: Copyright Snowbound Software 1998<br>
  JpegInterchangeFormat: 179051<br>
<br>
</code></pre>
<h3>f505d8aaa96b8da1a1c92363b898f97a.tif</h3>

<ul><li>Origin: <code>http://korejtko.net/wp-content/uploads/2008/11/148222981.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Image Width: 350 Image Length: 233<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 233<br>
  Planar Configuration: single image plane<br>
  Software: Capture NX 2.0.0 W<br>
  DateTime: 2008:11:11 22:18:57<br>
  XMLPacket (XMP Metadata): Present<br>
  EXIFIFDOffset: 0x8397<br>
  ICC Profile: &lt;present&gt;, 2756 bytes<br>
TIFF Directory at offset 0x8397 (33687)<br>
  ExifVersion: 0x30,0x32,0x32,0x30<br>
  MakerNote: 0x4e,0x69,0x6b,0x6f,0x6e,0x0,0x2,0x0,0x0,0x0,0x49,0x49,0x2a,0x0,0x8,0x0,0x0,0x0,0x7,0x0,0x1,0x0,0x7,0x0,0x4,0x0,0x0,0x0,0x30,0x32,0x31,0x30,0x11,0x0,0x4,0x0,0x1,0x0,0x0,0x0,0xd4,0x0,0x0,0x0,0xa1,0x0,0x7,0x0,0x38,0x0,0x0,0x0,0x62,0x0,0x0,0x0,0x9,0xe,0x2,0x0,0x13,0x0,0x0,0x0,0x9a,0x0,0x0,0x0,0xe,0xe,0x7,0x0,0x1e,0x0,0x0,0x0,0xae,0x0,0x0,0x0,0x10,0xe,0x4,0x0,0x1,0x0,0x0,0x0,0x32,0x1,0x0,0x0,0x22,0xe,0x3,0x0,0x4,0x0,0x0,0x0,0xcc,0x0,0x0,0x0,0x0,0x0,0x0,0x0,0x2b,0x65,0x4,0x0,0x30,0x0,0x0,0x0,0x42,0x41,0x3d,0x50,0x4f,0x4c,0x4f,0x4e,0x4b,0x4f,0x4e,0x4b,0x50,0x4f,0x4c,0x51,0x50,0x4d,0x52,0x50,0x4d,0x52,0x51,0x4e,0x52,0x51,0x4e,0x53,0x52,0x4e,0x53,0x52,0x4e,0x54,0x53,0x4f,0x55,0x53,0x4f,0x55,0x54,0x50,0x56,0x54,0x50,0x56,0x55,0x51,0x43,0x61,0x70,0x74,0x75,0x72,0x65,0x20,0x4e,0x58,0x20,0x32,0x2e,0x30,0x2e,0x30,0x20,0x57,0x0,0x33,0x30,0x31,0x30,0x30,0x2,0x0,0x1,0x0,0x0,0x0,0xf,0x85,0x0,0x0,0x0,0x0,0x0,0x1,0x2,0x0,0x0,0x0,0xab,0x84,0x0,0x0,0x0,0x0,0x1,0x1,0x8,0x0,0x8,0x0<br>
  FlashpixVersion: 0x30,0x31,0x30,0x30<br>
  ColorSpace: 65535<br>
TIFF Directory at offset 0x850f (34063)<br>
  Image Width: 160 Image Length: 106<br>
  Resolution: 72, 72 pixels/inch<br>
  Bits/Sample: 8<br>
  Compression Scheme: None<br>
  Photometric Interpretation: RGB color<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 106<br>
  Planar Configuration: single image plane<br>
<br>
</code></pre>
<h3>m1-f55287249b20fd368b4683f8336153d3.tif</h3>

<h3>m2-f55287249b20fd368b4683f8336153d3.tif</h3>

<ul><li>Origin: <code>http://www.aibsnleawbtc.org/appeal1.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-f55287249b20fd368b4683f8336153d3.tif:<br>
TIFF Directory at offset 0x9fac (40876)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1728 Image Length: 1137<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: min-is-black<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 56<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-0<br>
  Software: Windows NT Fax Server<br>
  Predictor: none 1 (0x1)<br>
m2-f55287249b20fd368b4683f8336153d3.tif:<br>
TIFF Directory at offset 0x9fac (40876)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 1728 Image Length: 1137<br>
  Resolution: 204, 98 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: min-is-black<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 56<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-0<br>
  Software: Windows NT Fax Server<br>
  Predictor: none 1 (0x1)<br>
<br>
</code></pre>
<h3>f8179f8f5e566349cf3583a1ff3ea95c.tif</h3>

<ul><li>Origin: <code>http://www.mdu.edu.tw/~oga/news/052901.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x97d2 (38866)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x1d8d2 (121042)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x2bc6a (179306)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x3a75e (239454)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 3-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x4e12c (319788)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 4-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x5f768 (391016)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 5-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x74484 (476292)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 6-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x89a64 (563812)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 7-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0x9d51e (644382)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 8-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0xaa530 (697648)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 9-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
TIFF Directory at offset 0xb21b2 (729522)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1656 Image Length: 2339<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 1<br>
  Compression Scheme: CCITT Group 3<br>
  Photometric Interpretation: min-is-white<br>
  Thresholding: bilevel art scan<br>
  FillOrder: lsb-to-msb<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 2339<br>
  Min Sample Value: 0<br>
  Max Sample Value: 1<br>
  Planar Configuration: single image plane<br>
  Page Number: 10-11<br>
  Make: RICOH<br>
  Group 3 Options: (0 = 0x0)<br>
<br>
</code></pre>
<h3>fa0aa927763ee4c7ebf43a5d05dfebc7.tif</h3>

<ul><li>Origin: <code>http://planningdevelopment.easthants.gov.uk/docsonlinefiles/62614_1.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x8 (8)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1752 Image Length: 2352<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2352<br>
  Planar Configuration: single image plane<br>
  Page Number: 0-12<br>
  DocumentName: DN0PUnknown serial  1222238320      350800000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:01<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x36d6 (14038)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1752 Image Length: 2354<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2354<br>
  Planar Configuration: single image plane<br>
  Page Number: 1-12<br>
  DocumentName: DN0PUnknown serial  1222238320      350900000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:03<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x930e (37646)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1750 Image Length: 2352<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2352<br>
  Planar Configuration: single image plane<br>
  Page Number: 2-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351000000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:05<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x14934 (84276)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1748 Image Length: 2352<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2352<br>
  Planar Configuration: single image plane<br>
  Page Number: 3-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351100000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:06<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x1c5e6 (116198)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1750 Image Length: 2354<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2354<br>
  Planar Configuration: single image plane<br>
  Page Number: 4-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351200000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:07<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x2494a (149834)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1752 Image Length: 2352<br>
  Resolution: 200, 200<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 1, 2<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2352<br>
  Planar Configuration: single image plane<br>
  Page Number: 5-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351300000.----!--<br>
  Make: VendorID<br>
  Model: ProductID<br>
  Software: xVCS V3.5      <br>
  DateTime: ******************=<br>
  Artist: IRIS 2001          <br>
  JpegInterchangeFormat: 150324<br>
  JpegInterchangeFormatLength: 458524<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x94a50 (608848)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1752 Image Length: 2354<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2354<br>
  Planar Configuration: single image plane<br>
  Page Number: 6-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351400000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:13<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0x9c6e0 (640736)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1754 Image Length: 2356<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2356<br>
  Planar Configuration: single image plane<br>
  Page Number: 7-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351500000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:17<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0xa03b2 (656306)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1752 Image Length: 2348<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2348<br>
  Planar Configuration: single image plane<br>
  Page Number: 8-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351600000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:18<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0xaac18 (699416)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 1754 Image Length: 2350<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2350<br>
  Planar Configuration: single image plane<br>
  Page Number: 9-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351700000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:21<br>
  Artist: IRIS 2001          <br>
TIFF Directory at offset 0xb480e (739342)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 3518 Image Length: 2358<br>
  Resolution: 200, 200<br>
  Bits/Sample: 8<br>
  Compression Scheme: Old-style JPEG<br>
  Photometric Interpretation: YCbCr<br>
  YCbCr Subsampling: 1, 2<br>
  Samples/Pixel: 3<br>
  Rows/Strip: 2358<br>
  Planar Configuration: single image plane<br>
  Page Number: 10-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351800000.----!--<br>
  Make: VendorID<br>
  Model: ProductID<br>
  Software: xVCS V3.5      <br>
  DateTime: ******************=<br>
  Artist: IRIS 2001          <br>
  JpegInterchangeFormat: 739832<br>
  JpegInterchangeFormatLength: 760181<br>
  JpegProc: 1<br>
  JpegRestartInterval: 0<br>
TIFF Directory at offset 0x16e36e (1500014)<br>
  Subfile Type: multi-page document (2 = 0x2)<br>
  Image Width: 3516 Image Length: 2360<br>
  Resolution: 200, 200<br>
  Compression Scheme: CCITT Group 4<br>
  Photometric Interpretation: min-is-white<br>
  Rows/Strip: 2360<br>
  Planar Configuration: single image plane<br>
  Page Number: 11-12<br>
  DocumentName: DN0PUnknown serial  1222238320      351900000.----!--<br>
  Make: Kodak<br>
  Model: Kodak i200<br>
  Software: xVCS V3.5      <br>
  DateTime: 2008:09:24 10:19:37<br>
  Artist: IRIS 2001          <br>
<br>
</code></pre>
<h3>m1-fe50c06bcf744c640005967082a93ead.tif</h3>

<ul><li>Origin: <code>http://www.arkansashighways.com/maps/counties/mlafa.tif</code></li></ul>

<h4>Notes</h4>

<pre><code>TIFF Directory at offset 0x175aba (1530554)<br>
  Subfile Type: (0 = 0x0)<br>
  Image Width: 7200 Image Length: 12000<br>
  Resolution: 200, 200 pixels/inch<br>
  Bits/Sample: 96<br>
  Compression Scheme: LZW<br>
  Photometric Interpretation: min-is-black<br>
  Thresholding: error diffused<br>
  Orientation: row 0 top, col 0 lhs<br>
  Samples/Pixel: 1<br>
  Rows/Strip: 13<br>
  Planar Configuration: single image plane<br>
  Make: Oce<br>
  DateTime: 2007:08:27 09:03:28<br>
  TargetPrinter: <br>
<br>
</code></pre>
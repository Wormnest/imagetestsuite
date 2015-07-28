# Introduction #

The PNG testsuite is a collection of [PNG images](http://en.wikipedia.org/wiki/Portable_Network_Graphics) from publicly available
sources, intended to help verify the correct operation of PNG image
decoders when presented with malformed or esoteric characteristics.

It is not the intention of this testsuite to verify the correct rendering of
images, but rather to ensure safe operation when presented with malformed
data, esoteric characteristics, edge cases, and pathological input. If you're interested in verifying correct rendering, you should check out the official PNG testsuite, [PngSuite](http://www.schaik.com/pngsuite/).

Your decoder or application should gracefully handle any errors while
attempting to render these images. To read more about how these testsuites are
generated and their intended use, see AboutTestSuite.

# Specification #

These images were selected based on the number of execution paths explored with [libpng-1.2.34](http://www.libpng.org/pub/png/libpng.html). As every png chunk includes a 32bit CRC, in order to ensure good coverage using mutated data, it was necessary to test using the libpng API `png_set_crc_action(PNG_CRC_QUIET_USE, PNG_CRC_QUIET_USE)`. To maximise coverage in decoders which legitimately discard bad chunks, test images are provided in both an original and corrected form where appropriate.

Approximately 4295 unique lines of code are executed when decoding the
testsuite using libpng-1.2.34.

## Coverage ##

  * Using the pngtest utility from the libpng distribution, of the 9139 total lines, 4295 are executed (~50%).

![http://chart.apis.google.com/chart?chs=500x250&chd=t:287,81,330,99,559,28,104,1882,596,319,10,0&chl=png.c|pngerror.c|pngget.c|pngmem.c|pngread.c|pngrio.c|pngrtran.c|pngrutil.c|pngset.c|pngtest.c|pngtrans.c|sysmacros.h&cht=p&chtt=Distribution%20of%20Executed%20Lines%20by%20File&ft=.png](http://chart.apis.google.com/chart?chs=500x250&chd=t:287,81,330,99,559,28,104,1882,596,319,10,0&chl=png.c|pngerror.c|pngget.c|pngmem.c|pngread.c|pngrio.c|pngrtran.c|pngrutil.c|pngset.c|pngtest.c|pngtrans.c|sysmacros.h&cht=p&chtt=Distribution%20of%20Executed%20Lines%20by%20File&ft=.png)
![http://chart.apis.google.com/chart?chs=500x250&chd=t:150,115,345,47,337,7,2823,325,232,102,352,9&chl=png.c|pngerror.c|pngget.c|pngmem.c|pngread.c|pngrio.c|pngrtran.c|pngrutil.c|pngset.c|pngtest.c|pngtrans.c|sysmacros.h&cht=p&chtt=Distribution%20of%20Unexecuted%20Lines%20by%20File&ft=.png](http://chart.apis.google.com/chart?chs=500x250&chd=t:150,115,345,47,337,7,2823,325,232,102,352,9&chl=png.c|pngerror.c|pngget.c|pngmem.c|pngread.c|pngrio.c|pngrtran.c|pngrutil.c|pngset.c|pngtest.c|pngtrans.c|sysmacros.h&cht=p&chtt=Distribution%20of%20Unexecuted%20Lines%20by%20File&ft=.png)
![http://chart.apis.google.com/chart?chds=0,3000&chs=500x250&cht=bvs&chco=4D89F9,C6D9FD&chd=t:287,81,330,99,559,28,104,1882,596,319,10,0|150,115,345,47,337,7,2823,325,232,102,352,9&cht=bvs&chtt=Executed%20vs%20Unexecuted%20Lines%20Per%20File&ft=.png](http://chart.apis.google.com/chart?chds=0,3000&chs=500x250&cht=bvs&chco=4D89F9,C6D9FD&chd=t:287,81,330,99,559,28,104,1882,596,319,10,0|150,115,345,47,337,7,2823,325,232,102,352,9&cht=bvs&chtt=Executed%20vs%20Unexecuted%20Lines%20Per%20File&ft=.png)

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
<pre><code>c-m8-d41d8cd98f00b204e9800998ecf8427e.png<br>
</code></pre>

This is an 8th generation mutation of a source image with checksum<br>
d41d8cd98f00b204e9800998ecf8427e, and at least one chunk's checksum has been<br>
corrected.<br>
<br>
An origin containing "brokensuite" indicates the original source image is<br>
derived from a testcase provided by the excellent<br>
<a href='http://code.google.com/p/javapng/'>sixlegs java png decoding library</a>. These<br>
images do not contain any artistic content, but the project publishes them<br>
under the LGPL.<br>
<br>
<h2>Images</h2>

<h3>008b8bb75b8a487dc5aac86c9abb06fb.png FT</h3>

<ul><li>Origin: <code>brokensuite:multiple_sbit.png</code></li></ul>

<h4>Notes</h4>

<pre><code>008b8bb75b8a487dc5aac86c9abb06fb.png  multiple sBIT not allowed<br>
ERROR: 008b8bb75b8a487dc5aac86c9abb06fb.png<br>
<br>
</code></pre>
<h3>0132cfdbd8ca323574a2072e7ed5014c.png FT</h3>

<ul><li>Origin: <code>brokensuite:multiple_srgb.png</code></li></ul>

<h4>Notes</h4>

<pre><code>0132cfdbd8ca323574a2072e7ed5014c.png  multiple sRGB not allowed<br>
ERROR: 0132cfdbd8ca323574a2072e7ed5014c.png<br>
<br>
</code></pre>
<h3>0301fde58080883e938b604cab9768ea.png FT</h3>

<ul><li>Origin: <code>brokensuite:srgb_after_plte.png</code></li></ul>

<h4>Notes</h4>

<pre><code>0301fde58080883e938b604cab9768ea.png  sRGB must precede PLTE<br>
ERROR: 0301fde58080883e938b604cab9768ea.png<br>
<br>
</code></pre>
<h3>m1-04c2707d63235dd5ab2c66ee98a36521.png TO</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<ul><li>Image is damaged beyond recognition, some french text is visible.</li></ul>

<pre><code>m1-04c2707d63235dd5ab2c66ee98a36521.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-04c2707d63235dd5ab2c66ee98a36521.png  zlib: inflate error = -3 (data error)<br>
m1-04c2707d63235dd5ab2c66ee98a36521.png  private, critical chunk IyND (warning)<br>
ERROR: m1-04c2707d63235dd5ab2c66ee98a36521.png<br>
<br>
</code></pre>
<h3>c-m2-0699098e769a2d80e60f33dbb3332b61.png TO</h3>

<h3>m1-0699098e769a2d80e60f33dbb3332b61.png TO</h3>

<h3>m2-0699098e769a2d80e60f33dbb3332b61.png TO</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<ul><li>Image is damaged beyond recognition</li></ul>

<pre><code>c-m2-0699098e769a2d80e60f33dbb3332b61.png  invalid pHYs unit specifier (147)<br>
c-m2-0699098e769a2d80e60f33dbb3332b61.png  tEXt text contains NULL character(s)<br>
c-m2-0699098e769a2d80e60f33dbb3332b61.png  zlib: inflate error = -3 (data error)<br>
c-m2-0699098e769a2d80e60f33dbb3332b61.png  illegal (unless recently approved) unknown, public chunk iEND<br>
ERROR: c-m2-0699098e769a2d80e60f33dbb3332b61.png<br>
m1-0699098e769a2d80e60f33dbb3332b61.png  first chunk must be IHDR<br>
m1-0699098e769a2d80e60f33dbb3332b61.png  illegal (unless recently approved) unknown, public chunk sHDR<br>
m1-0699098e769a2d80e60f33dbb3332b61.png  first chunk must be IHDR<br>
m1-0699098e769a2d80e60f33dbb3332b61.png  EOF while reading pHYs data<br>
ERROR: m1-0699098e769a2d80e60f33dbb3332b61.png<br>
m2-0699098e769a2d80e60f33dbb3332b61.png  invalid pHYs unit specifier (147)<br>
m2-0699098e769a2d80e60f33dbb3332b61.png  CRC error in chunk pHYs (computed ccdc8c94, expected d2dd7efc)<br>
m2-0699098e769a2d80e60f33dbb3332b61.png  tEXt text contains NULL character(s)<br>
m2-0699098e769a2d80e60f33dbb3332b61.png  zlib: inflate error = -3 (data error)<br>
m2-0699098e769a2d80e60f33dbb3332b61.png  illegal (unless recently approved) unknown, public chunk iEND<br>
ERROR: m2-0699098e769a2d80e60f33dbb3332b61.png<br>
Errors were detected in 3 of the 3 files tested.<br>
<br>
</code></pre>
<h3>073c98872b81d1004d750f18a4b5f732.png FT</h3>

<ul><li>Origin: <code>brokensuite:length_ster.png</code></li></ul>

<h4>Notes</h4>

<pre><code>073c98872b81d1004d750f18a4b5f732.png  invalid sTER length<br>
ERROR: 073c98872b81d1004d750f18a4b5f732.png<br>
<br>
</code></pre>
<h3>0839d93f8e77e21acd0ac40a80b14b7b.png U</h3>

<ul><li>Origin: <code>http://img504.imageshack.us/img504/7096/gilgagennaiohx6.png</code></li></ul>

<h4>Notes</h4>

<ul><li>Adobe Photoshop CS2 Windows<br>
</li><li>Image is unlikely to be free to use, replacement welcome.</li></ul>

<pre><code>OK: 0839d93f8e77e21acd0ac40a80b14b7b.png (350x490, 24-bit RGB, non-interlaced, -2.5%).<br>
<br>
</code></pre>
<h3>0b7d50ac449fd59eb3de00647636d0c9.png FT</h3>

<ul><li>Origin: <code>brokensuite:length_chrm.png</code></li></ul>

<h4>Notes</h4>

<pre><code>0b7d50ac449fd59eb3de00647636d0c9.png  invalid cHRM length<br>
ERROR: 0b7d50ac449fd59eb3de00647636d0c9.png<br>
<br>
</code></pre>
<h3>0d466db9067b719df0b06ef441bf1ee7.png FT</h3>

<ul><li>Origin: <code>brokensuite:multiple_iccp.png</code></li></ul>

<h4>Notes</h4>

<pre><code>0d466db9067b719df0b06ef441bf1ee7.png  multiple iCCP not allowed<br>
ERROR: 0d466db9067b719df0b06ef441bf1ee7.png<br>
<br>
</code></pre>
<h3>c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png TU</h3>

<h3>m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png TU</h3>

<ul><li>Origin: <code>http://www.alkaka.com/imeg/Internet/1.PNG</code></li></ul>

<h4>Notes</h4>

<ul><li>Images are damaged beyond recognition, but derived from likely non-free image. Replacement welcome.</li></ul>

<pre><code>c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (141) (warning)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (242) (warning)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  invalid IDAT row-filter type (7)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (227) (warning)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  invalid IDAT row-filter type (14)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  invalid IDAT row-filter type (9)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  zlib: inflate error = -3 (data error)<br>
c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  EOF while reading tIME data<br>
ERROR: c-m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  CRC error in chunk IDAT (computed dae1adb2, expected 1132e69e)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  CRC error in chunk IDAT (computed 0a15515f, expected 9dbadf56)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  CRC error in chunk IDAT (computed 4fc1e207, expected 3f04b634)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (141) (warning)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (242) (warning)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  invalid IDAT row-filter type (7)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  CRC error in chunk IDAT (computed 6d2ad651, expected 8001598b)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  private (invalid?) IDAT row-filter type (227) (warning)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  invalid IDAT row-filter type (14)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  CRC error in chunk IDAT (computed ed29880b, expected 1d9b84e6)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  invalid IDAT row-filter type (9)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  CRC error in chunk IDAT (computed b6e19be7, expected 3e0634d3)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  zlib: inflate error = -3 (data error)<br>
m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png  EOF while reading tIME data<br>
ERROR: m1-125cdc39e13ce7c237b7b4a9e1d8f21c.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>138331052d7c6e4acebfaa92af314e12.png FT</h3>

<ul><li>Origin: <code>brokensuite:length_hist.png</code></li></ul>

<h4>Notes</h4>

<pre><code>138331052d7c6e4acebfaa92af314e12.png  invalid number of hIST entries (14)<br>
ERROR: 138331052d7c6e4acebfaa92af314e12.png<br>
<br>
</code></pre>
<h3>13f665c09e4b03cdbe2fff3015ec8aa7.png FT</h3>

<ul><li>Origin: <code>brokensuite:multiple_bkgd.png</code></li></ul>

<h4>Notes</h4>

<pre><code>13f665c09e4b03cdbe2fff3015ec8aa7.png  multiple bKGD not allowed<br>
ERROR: 13f665c09e4b03cdbe2fff3015ec8aa7.png<br>
<br>
</code></pre>
<h3>18288f761922f9b9b00e927eaeb9e707.png T</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<ul><li>Crashes pngcheck -f<br>
</li><li>Damaged beyond recognition</li></ul>


<pre><code>Segmentation Fault<br>
</code></pre>
<h3>18bd8bf75e7a9b40b961dd501654ce0e.png TF</h3>

<ul><li>Origin: <code>brokensuite:hist_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>18bd8bf75e7a9b40b961dd501654ce0e.png  hIST must precede IDAT<br>
ERROR: 18bd8bf75e7a9b40b961dd501654ce0e.png<br>
<br>
</code></pre>
<h3>18f9baf3834980f4b80a3e82ad45be48.png U</h3>

<ul><li>Origin: <code>http://muziektheaterapplaus.nl/algemeen/templates/oliver/images/MuziekTheaterApplaus.png</code></li></ul>

<h4>Notes</h4>

<ul><li>Software: ULead System</li></ul>

<pre><code>OK: 18f9baf3834980f4b80a3e82ad45be48.png (118x79, 24-bit RGB, interlaced, 62.3%).<br>
<br>
</code></pre>
<h3>c-m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png TU</h3>

<h3>m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png TU</h3>

<ul><li>Origin: <code>http://www.jbiconnect.org/locale/en_AU/images/banner_right_connect.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk mkBT (computed 28db6e2e, expected 52da2a66)<br>
c-m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk IHDR (computed e0d16056, expected 97d650c0)<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk mkTS (computed 844a7acb, expected 052610e6)<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk mkBT (computed a083d4c3, expected e0bf25a3)<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk mkBT (computed 80d73f6d, expected eb77bd16)<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk mkBT (computed 6c1f44fb, expected d93b8e9c)<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk mkBT (computed 28db6e2e, expected 52da2a66)<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  CRC error in chunk mkBT (computed ecd1c296, expected 7729a6f7)<br>
m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-19e0d1d0dfe97dca39e9d449c6b8b3d2.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>1ae14e57b7062597279134ff2eeb39c0.png FT</h3>

<ul><li>Origin: <code>brokensuite:multiple_trns.png</code></li></ul>

<h4>Notes</h4>

<pre><code>1ae14e57b7062597279134ff2eeb39c0.png  multiple tRNS not allowed<br>
ERROR: 1ae14e57b7062597279134ff2eeb39c0.png<br>
<br>
</code></pre>
<h3>m1-1b5df699719c4a7cc8314ab9af139405.png U</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<ul><li>Image is damaged beyond recognition, an outline of a face is visible.</li></ul>

<pre><code>m1-1b5df699719c4a7cc8314ab9af139405.png  invalid IDAT row-filter type (119)<br>
m1-1b5df699719c4a7cc8314ab9af139405.png  private (invalid?) IDAT row-filter type (173) (warning)<br>
m1-1b5df699719c4a7cc8314ab9af139405.png  private (invalid?) IDAT row-filter type (224) (warning)<br>
m1-1b5df699719c4a7cc8314ab9af139405.png  invalid IDAT row-filter type (90)<br>
m1-1b5df699719c4a7cc8314ab9af139405.png  invalid IDAT row-filter type (107)<br>
m1-1b5df699719c4a7cc8314ab9af139405.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-1b5df699719c4a7cc8314ab9af139405.png<br>
<br>
</code></pre>
<h3>1b9a48cf04466108f6f2d225d100edbf.png TF</h3>

<ul><li>Origin: <code>brokensuite:pcal_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>1b9a48cf04466108f6f2d225d100edbf.png  sCAL must precede IDAT<br>
1b9a48cf04466108f6f2d225d100edbf.png  pHYs must precede IDAT<br>
1b9a48cf04466108f6f2d225d100edbf.png  pCAL must precede IDAT<br>
ERROR: 1b9a48cf04466108f6f2d225d100edbf.png<br>
<br>
</code></pre>
<h3>1bcc34d49e56a2fba38490db206328b8.png TF</h3>

<ul><li>Origin: <code>brokensuite:multiple_scal.png</code></li></ul>

<h4>Notes</h4>

<pre><code>1bcc34d49e56a2fba38490db206328b8.png  multiple sCAL not allowed<br>
ERROR: 1bcc34d49e56a2fba38490db206328b8.png<br>
<br>
</code></pre>
<h3>1ebd73c1d3fbc89782f29507364128fc.png O</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<ul><li>Origin unknown, but likely non-free. Contains the text "leeroy" and photograph of a man.</li></ul>

<pre><code>OK: 1ebd73c1d3fbc89782f29507364128fc.png (110x110, 24-bit RGB, non-interlaced, -54.6%).<br>
<br>
</code></pre>
<h3>c-m1-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>c-m2-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>c-m3-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>c-m5-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>c-m6-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>c-m7-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>c-m8-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m1-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m2-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m3-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m4-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m5-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m6-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m7-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<h3>m8-1f97f040d0b6b26faeb0a1a7f1499590.png TO</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<ul><li>Damaged beyond recognition.</li></ul>

<pre><code>c-m1-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m1-1f97f040d0b6b26faeb0a1a7f1499590.png  invalid sCAL length<br>
c-m1-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading Imag data<br>
ERROR: c-m1-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
c-m2-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m2-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
c-m2-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: c-m2-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
c-m3-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m3-1f97f040d0b6b26faeb0a1a7f1499590.png  invalid sCAL unit specifier (67)<br>
c-m3-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
c-m3-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: c-m3-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
c-m5-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m5-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
c-m5-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: c-m5-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
c-m6-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m6-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk IFND<br>
ERROR: c-m6-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
c-m7-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m7-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
c-m7-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: c-m7-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
c-m8-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m8-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
c-m8-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: c-m8-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m1-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk IHDR (computed dd10c7bd, expected f87b9861)<br>
m1-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m1-1f97f040d0b6b26faeb0a1a7f1499590.png  invalid sCAL length<br>
m1-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading Imag data<br>
ERROR: m1-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m2-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk IHDR (computed dd10c7bd, expected f87b9861)<br>
m2-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk pHYs (computed 91a71c6f, expected 9df55a60)<br>
m2-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk vpAg (computed 0d8f0029, expected 09c59193)<br>
m2-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m2-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
m2-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: m2-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m3-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk IHDR (computed dd10c7bd, expected f87b9861)<br>
m3-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk pHYs (computed 91a71c6f, expected 9df55a60)<br>
m3-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk vpAg (computed 0d8f0029, expected 09c59193)<br>
m3-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m3-1f97f040d0b6b26faeb0a1a7f1499590.png  invalid sCAL unit specifier (67)<br>
m3-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
m3-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: m3-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  first chunk must be IHDR<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk dHDR<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  first chunk must be IHDR<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk bHYs<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  first chunk must be IHDR<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  first chunk must be IHDR<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  invalid sCAL unit specifier (67)<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  first chunk must be IHDR<br>
m4-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: m4-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m5-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk IHDR (computed dd10c7bd, expected f87b9861)<br>
m5-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk oFFs (computed ec472581, expected 45a5f521)<br>
m5-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk pHYs (computed 91a71c6f, expected 9df55a60)<br>
m5-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk vpAg (computed 0d8f0029, expected 09c59193)<br>
m5-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m5-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
m5-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: m5-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m6-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk vpAg (computed cda26ea1, expected 09c59193)<br>
m6-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m6-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk IFND<br>
ERROR: m6-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m7-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk IHDR (computed dd10c7bd, expected f87b9861)<br>
m7-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk pHYs (computed 91a71c6f, expected 9df55a60)<br>
m7-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk vpAg (computed 0d8f0029, expected 09c59193)<br>
m7-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m7-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
m7-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: m7-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
m8-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk IHDR (computed dd10c7bd, expected f87b9861)<br>
m8-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk pHYs (computed 91a71c6f, expected 9df55a60)<br>
m8-1f97f040d0b6b26faeb0a1a7f1499590.png  CRC error in chunk vpAg (computed 0d8f0029, expected 09c59193)<br>
m8-1f97f040d0b6b26faeb0a1a7f1499590.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m8-1f97f040d0b6b26faeb0a1a7f1499590.png:  invalid chunk name " by " (20 62 79 20)<br>
m8-1f97f040d0b6b26faeb0a1a7f1499590.png  EOF while reading  by  data<br>
ERROR: m8-1f97f040d0b6b26faeb0a1a7f1499590.png<br>
Errors were detected in 15 of the 15 files tested.<br>
<br>
</code></pre>
<h3>c-m1-1fc0c0de88608a9445d6f98a544b5abc.png TU</h3>

<h3>m1-1fc0c0de88608a9445d6f98a544b5abc.png TU</h3>

<ul><li>Origin: <code>http://www.dayandnight.lv/images/techn/back_en.png</code></li></ul>

<h4>Notes</h4>

<ul><li>Likely non-free, but trivial contents.</li></ul>

<pre><code>c-m1-1fc0c0de88608a9445d6f98a544b5abc.png  tEXt keyword is longer than 79 characters<br>
c-m1-1fc0c0de88608a9445d6f98a544b5abc.png  iTXt keyword is longer than 79 characters<br>
c-m1-1fc0c0de88608a9445d6f98a544b5abc.png  private, critical chunk IdND (warning)<br>
c-m1-1fc0c0de88608a9445d6f98a544b5abc.png  file doesn't end with an IEND chunk<br>
ERROR: c-m1-1fc0c0de88608a9445d6f98a544b5abc.png<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  tEXt keyword is longer than 79 characters<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  CRC error in chunk mkTS (computed 0e7e8c98, expected eda6716d)<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  CRC error in chunk mkBT (computed 6c7f5095, expected 3f7455f9)<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  CRC error in chunk mkBT (computed fd3d7288, expected add7a3c2)<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  CRC error in chunk mkBT (computed e206b6a6, expected 7729a6f7)<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  iTXt keyword is longer than 79 characters<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  CRC error in chunk iTXt (computed 32bfd0de, expected aa50e890)<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  private, critical chunk IdND (warning)<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  CRC error in chunk IdND (computed 97cd4c55, expected ae426082)<br>
m1-1fc0c0de88608a9445d6f98a544b5abc.png  file doesn't end with an IEND chunk<br>
ERROR: m1-1fc0c0de88608a9445d6f98a544b5abc.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>c-m2-272ae9468b7883e5cf61873a17271fb4.png TO</h3>

<h3>m1-272ae9468b7883e5cf61873a17271fb4.png TO</h3>

<h3>m2-272ae9468b7883e5cf61873a17271fb4.png TO</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<ul><li>Damaged beyond recognition.</li></ul>

<pre><code>c-m2-272ae9468b7883e5cf61873a17271fb4.png  private (invalid?) IDAT row-filter type (213) (warning)<br>
c-m2-272ae9468b7883e5cf61873a17271fb4.png  invalid IDAT row-filter type (124)<br>
c-m2-272ae9468b7883e5cf61873a17271fb4.png  invalid zTXt compression method (120)<br>
c-m2-272ae9468b7883e5cf61873a17271fb4.png  illegal reserved-bit-set chunk zTot<br>
c-m2-272ae9468b7883e5cf61873a17271fb4.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
c-m2-272ae9468b7883e5cf61873a17271fb4.png:  invalid chunk name "I�ND" (49 ffffffd0 4e 44)<br>
c-m2-272ae9468b7883e5cf61873a17271fb4.png  illegal (unless recently approved) unknown, public chunk I�ND<br>
ERROR: c-m2-272ae9468b7883e5cf61873a17271fb4.png<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  illegal (unless recently approved) unknown, public chunk sRGd<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  private (invalid?) IDAT row-filter type (208) (warning)<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  private (invalid?) IDAT row-filter type (211) (warning)<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  private (invalid?) IDAT row-filter type (206) (warning)<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  private (invalid?) IDAT row-filter type (153) (warning)<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  invalid IDAT row-filter type (37)<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  invalid zTXt compression method (120)<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  illegal reserved-bit-set chunk zTot<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
m1-272ae9468b7883e5cf61873a17271fb4.png:  invalid chunk name "I�ND" (49 ffffffd0 4e 44)<br>
m1-272ae9468b7883e5cf61873a17271fb4.png  illegal (unless recently approved) unknown, public chunk I�ND<br>
ERROR: m1-272ae9468b7883e5cf61873a17271fb4.png<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  private (invalid?) IDAT row-filter type (213) (warning)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  invalid IDAT row-filter type (124)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  CRC error in chunk IDAT (computed bc293aba, expected 81be9b02)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  CRC error in chunk zTXt (computed a6ccd434, expected 98310798)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  CRC error in chunk zTXt (computed 62b9ea06, expected 0c12e284)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  CRC error in chunk zTXt (computed 810f8596, expected 810fd196)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  invalid zTXt compression method (120)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  CRC error in chunk zTXt (computed 5fc2f3c2, expected 5f3947e2)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  illegal reserved-bit-set chunk zTot<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
m2-272ae9468b7883e5cf61873a17271fb4.png:  invalid chunk name "I�ND" (49 ffffffd0 4e 44)<br>
m2-272ae9468b7883e5cf61873a17271fb4.png  illegal (unless recently approved) unknown, public chunk I�ND<br>
ERROR: m2-272ae9468b7883e5cf61873a17271fb4.png<br>
Errors were detected in 3 of the 3 files tested.<br>
<br>
</code></pre>
<h3>2a6ff5f8106894b22dad3ce99673481a.png U</h3>

<ul><li>Origin: <code>http://magnet.caltech.edu/images/m7.png</code></li></ul>

<h4>Notes</h4>

<pre><code>2a6ff5f8106894b22dad3ce99673481a.png  iCCP not allowed with sRGB<br>
ERROR: 2a6ff5f8106894b22dad3ce99673481a.png<br>
<br>
</code></pre>
<h3>2d641a11233385bb37a524ff010a8531.png U</h3>

<ul><li>Origin: <code>http://www.coherentpdf.com/logo-cloud.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: 2d641a11233385bb37a524ff010a8531.png (162x159, 32-bit RGB+alpha, non-interlaced, 75.2%).<br>
<br>
</code></pre>
<h3>c-m1-2dc3bdd9274b121b851fa536b0e35b6a.png TO</h3>

<h3>c-m2-2dc3bdd9274b121b851fa536b0e35b6a.png TO</h3>

<h3>m1-2dc3bdd9274b121b851fa536b0e35b6a.png TO</h3>

<h3>m2-2dc3bdd9274b121b851fa536b0e35b6a.png TO</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid cHRM green point 13422.1 0.6<br>
c-m1-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid bKGD length<br>
c-m1-2dc3bdd9274b121b851fa536b0e35b6a.png  illegal reserved-bit-set chunk pHrs<br>
c-m1-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid chunk length (too large)<br>
ERROR: c-m1-2dc3bdd9274b121b851fa536b0e35b6a.png<br>
c-m2-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid cHRM blue point 168.296 0.42352<br>
c-m2-2dc3bdd9274b121b851fa536b0e35b6a.png  illegal reserved-bit-set chunk pHrs<br>
c-m2-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid chunk length (too large)<br>
ERROR: c-m2-2dc3bdd9274b121b851fa536b0e35b6a.png<br>
m1-2dc3bdd9274b121b851fa536b0e35b6a.png  CRC error in chunk IHDR (computed bb0c65a7, expected 3c0171e2)<br>
m1-2dc3bdd9274b121b851fa536b0e35b6a.png  CRC error in chunk gAMA (computed f37bf9ba, expected 0bfc6105)<br>
m1-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid cHRM green point 13422.1 0.6<br>
m1-2dc3bdd9274b121b851fa536b0e35b6a.png  CRC error in chunk cHRM (computed 8d71aff8, expected 9cba513c)<br>
m1-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid bKGD length<br>
m1-2dc3bdd9274b121b851fa536b0e35b6a.png  illegal reserved-bit-set chunk pHrs<br>
m1-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid chunk length (too large)<br>
ERROR: m1-2dc3bdd9274b121b851fa536b0e35b6a.png<br>
m2-2dc3bdd9274b121b851fa536b0e35b6a.png  CRC error in chunk IHDR (computed 03b002c2, expected 3c0171e2)<br>
m2-2dc3bdd9274b121b851fa536b0e35b6a.png  CRC error in chunk gAMA (computed f37bf9ba, expected 0bfc6105)<br>
m2-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid cHRM blue point 168.296 0.42352<br>
m2-2dc3bdd9274b121b851fa536b0e35b6a.png  CRC error in chunk cHRM (computed 42518ab3, expected 9cba513c)<br>
m2-2dc3bdd9274b121b851fa536b0e35b6a.png  CRC error in chunk oFFs (computed 70136083, expected fe75e54a)<br>
m2-2dc3bdd9274b121b851fa536b0e35b6a.png  illegal reserved-bit-set chunk pHrs<br>
m2-2dc3bdd9274b121b851fa536b0e35b6a.png  invalid chunk length (too large)<br>
ERROR: m2-2dc3bdd9274b121b851fa536b0e35b6a.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>31e3bc3eb811cff582b5feee2494fed8.png TF</h3>

<ul><li>Origin: <code>brokensuite:sbit_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>31e3bc3eb811cff582b5feee2494fed8.png  sBIT must precede IDAT<br>
ERROR: 31e3bc3eb811cff582b5feee2494fed8.png<br>
<br>
</code></pre>
<h3>3625f98e00148cdc136c53bdcd2d2e1e.png TO</h3>

<h3>c-3625f98e00148cdc136c53bdcd2d2e1e.png TO</h3>

<h3>c-m1-3625f98e00148cdc136c53bdcd2d2e1e.png TO</h3>

<h3>m1-3625f98e00148cdc136c53bdcd2d2e1e.png TO</h3>

<h3>m2-3625f98e00148cdc136c53bdcd2d2e1e.png TO</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
3625f98e00148cdc136c53bdcd2d2e1e.png  zero length sPLT palette name<br>
3625f98e00148cdc136c53bdcd2d2e1e.png  CRC error in chunk sPLT (computed 88723087, expected 8e000000)<br>
3625f98e00148cdc136c53bdcd2d2e1e.png:  invalid chunk name "A" (41 00 01 ffffff86)<br>
3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
3625f98e00148cdc136c53bdcd2d2e1e.png  EOF while reading A data<br>
ERROR: 3625f98e00148cdc136c53bdcd2d2e1e.png<br>
c-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
c-3625f98e00148cdc136c53bdcd2d2e1e.png  zero length sPLT palette name<br>
c-3625f98e00148cdc136c53bdcd2d2e1e.png:  invalid chunk name "A" (41 00 01 ffffff86)<br>
c-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
c-3625f98e00148cdc136c53bdcd2d2e1e.png  EOF while reading A data<br>
ERROR: c-3625f98e00148cdc136c53bdcd2d2e1e.png<br>
c-m1-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
c-m1-3625f98e00148cdc136c53bdcd2d2e1e.png  EOF while reading gAMA data<br>
ERROR: c-m1-3625f98e00148cdc136c53bdcd2d2e1e.png<br>
m1-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
m1-3625f98e00148cdc136c53bdcd2d2e1e.png  CRC error in chunk srLT (computed 158471d7, expected ce66668e)<br>
m1-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
m1-3625f98e00148cdc136c53bdcd2d2e1e.png  EOF while reading gAMA data<br>
ERROR: m1-3625f98e00148cdc136c53bdcd2d2e1e.png<br>
m2-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
m2-3625f98e00148cdc136c53bdcd2d2e1e.png  illegal reserved-bit-set chunk sPuT<br>
m2-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
m2-3625f98e00148cdc136c53bdcd2d2e1e.png  PLTE not allowed in INVALID image<br>
m2-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
m2-3625f98e00148cdc136c53bdcd2d2e1e.png  zlib: inflate error = -3 (data error)<br>
m2-3625f98e00148cdc136c53bdcd2d2e1e.png  first chunk must be IHDR<br>
ERROR: m2-3625f98e00148cdc136c53bdcd2d2e1e.png<br>
Errors were detected in 5 of the 5 files tested.<br>
<br>
</code></pre>
<h3>429104334d1fb6a58e17307883c17608.png TF</h3>

<ul><li>Origin: <code>brokensuite:sbit_after_plte.png</code></li></ul>

<h4>Notes</h4>

<pre><code>429104334d1fb6a58e17307883c17608.png  sBIT must precede PLTE<br>
ERROR: 429104334d1fb6a58e17307883c17608.png<br>
<br>
</code></pre>
<h3>42ec8668adb5dbc6581393f463976510.png TF</h3>

<ul><li>Origin: <code>brokensuite:trns_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>42ec8668adb5dbc6581393f463976510.png  tRNS must precede IDAT<br>
ERROR: 42ec8668adb5dbc6581393f463976510.png<br>
<br>
</code></pre>
<h3>4389427591c18bf36e748172640862c3.png TF</h3>

<ul><li>Origin: <code>brokensuite:ster_mode.png</code></li></ul>

<h4>Notes</h4>

<pre><code>4389427591c18bf36e748172640862c3.png  invalid sTER layout mode<br>
ERROR: 4389427591c18bf36e748172640862c3.png<br>
<br>
</code></pre>
<h3>463d3570f92a6b6ecba0cc4fd9a7a384.png TF</h3>

<ul><li>Origin: <code>brokensuite:multiple_plte.png</code></li></ul>

<h4>Notes</h4>

<pre><code>463d3570f92a6b6ecba0cc4fd9a7a384.png  multiple PLTE not allowed<br>
ERROR: 463d3570f92a6b6ecba0cc4fd9a7a384.png<br>
<br>
</code></pre>
<h3>c-m1-49e39033e275de9786d8c41f834c710b.png TO</h3>

<h3>m1-49e39033e275de9786d8c41f834c710b.png TO</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-49e39033e275de9786d8c41f834c710b.png  tRNS not allowed in grayscale+alpha image<br>
c-m1-49e39033e275de9786d8c41f834c710b.png  zlib: inflate error = -3 (data error)<br>
c-m1-49e39033e275de9786d8c41f834c710b.png  illegal (unless recently approved) unknown, public chunk tEND<br>
ERROR: c-m1-49e39033e275de9786d8c41f834c710b.png<br>
m1-49e39033e275de9786d8c41f834c710b.png  CRC error in chunk IHDR (computed dd8baef7, expected 4d9f902b)<br>
m1-49e39033e275de9786d8c41f834c710b.png  tRNS not allowed in grayscale+alpha image<br>
m1-49e39033e275de9786d8c41f834c710b.png  zlib: inflate error = -3 (data error)<br>
m1-49e39033e275de9786d8c41f834c710b.png  illegal (unless recently approved) unknown, public chunk tEND<br>
ERROR: m1-49e39033e275de9786d8c41f834c710b.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>4aae896ba900c48c63cffc0cc9f8c4dc.png TF</h3>

<ul><li>Origin: <code>http://www.schaik.com/pngsuite/x00n0g01.png</code>
</li><li>Origin: <code>brokensuite:x00n0g01.png</code></li></ul>

<h4>Notes</h4>

<pre><code>4aae896ba900c48c63cffc0cc9f8c4dc.png  invalid IHDR image dimensions (0x0)<br>
4aae896ba900c48c63cffc0cc9f8c4dc.png  file doesn't end with an IEND chunk<br>
ERROR: 4aae896ba900c48c63cffc0cc9f8c4dc.png<br>
<br>
</code></pre>
<h3>c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png</h3>

<h3>m1-4bdd87fd0324f0a3d84d6905d17e1731.png</h3>

<ul><li>Origin: <code>http://farm3.static.flickr.com/2401/2263329466_036c167f2e_o.png</code></li></ul>

<h4>Notes</h4>

<ul><li>A quick search doesn't reveal the flickr user who created this, as the license is usually published will update this if found.</li></ul>

<pre><code>c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid tIME year (0)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (45)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (150) (warning)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (124)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (114)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (127)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (131) (warning)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (22)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (133) (warning)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (36)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (199) (warning)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (242) (warning)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (6)<br>
c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-4bdd87fd0324f0a3d84d6905d17e1731.png<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid tIME year (0)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (45)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (150) (warning)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (124)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (114)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (127)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (131) (warning)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (22)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  CRC error in chunk IDAT (computed 1c93886a, expected 3577897a)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (133) (warning)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (36)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (199) (warning)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (242) (warning)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  invalid IDAT row-filter type (6)<br>
m1-4bdd87fd0324f0a3d84d6905d17e1731.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-4bdd87fd0324f0a3d84d6905d17e1731.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>4c5b82ba0a9c12356007bd71e52185b2.png</h3>

<ul><li>Origin: <code>http://www.riforma.it/pictures/frutta080321.png</code></li></ul>

<h4>Notes</h4>

<pre><code>4c5b82ba0a9c12356007bd71e52185b2.png  invalid sRGB length<br>
ERROR: 4c5b82ba0a9c12356007bd71e52185b2.png<br>
<br>
</code></pre>
<h3>4f14b7aab3a41855378c5517342598b9.png</h3>

<ul><li>Origin: <code>brokensuite:length_trns_palette.png</code></li></ul>

<h4>Notes</h4>

<pre><code>4f14b7aab3a41855378c5517342598b9.png  invalid tRNS length for palette image<br>
ERROR: 4f14b7aab3a41855378c5517342598b9.png<br>
<br>
</code></pre>
<h3>51a4d21670dc8dfa8ffc9e54afd62f5f.png</h3>

<ul><li>Origin: <code>http://www.carfolio.com/images/dbimages/zgas/manufacturers/id/5584/rolls-royce_logo.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: 51a4d21670dc8dfa8ffc9e54afd62f5f.png (160x278, 16-bit grayscale+alpha, interlaced, 71.4%).<br>
<br>
</code></pre>
<h3>c-m1-559dcf17d281e285b7f09f943b9706de.png</h3>

<h3>c-m2-559dcf17d281e285b7f09f943b9706de.png</h3>

<h3>m1-559dcf17d281e285b7f09f943b9706de.png</h3>

<h3>m2-559dcf17d281e285b7f09f943b9706de.png</h3>

<ul><li>Origin: <code>http://champions.mn/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://mapaurody.pl/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://adamvietnam.com/thegreatswim/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://santatividade.com.br/site/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.razorman.net/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.tcvb.org/site/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.floatsdown.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://master.weiqi.ru/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.gtk.ir/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://falcon-ua.cn/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.i-mh.net/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.friends4recovery.com/rainbow/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.obrazi.si//images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>https://www.scrapwords.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://map-online.fr/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://notesandgracenotes.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://7sana.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.topproducercampus.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://klikkelapagading.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.cafe.prijedor.ba/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://masterchong.com/v2/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://neutral-clan.net/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://portalmangabeira.com/v2/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.pato.chumporn.police.go.th/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://kuantancentral.com.my/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://angloisraeli.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.axcesstuscaloosa.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://belindarice.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://linboo.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.tyrol-webdesign.at/seidlschaar2/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://horrormoviekillers.com/mainsitearea/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.alsat.tv/eng/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.circleboost.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.kovaraw.com/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.verdehattrick.com.ar/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.bowhunternation.net/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.railpage.cz/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://goaaal.net/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://www.videoshqip.net/images/M_images/rating_star_blank.png</code>
</li><li>Origin: <code>http://bezboly.ru/templates/joomlafiles_green/images/rating_star_blank.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-559dcf17d281e285b7f09f943b9706de.png  invalid IDAT row-filter type (9)<br>
ERROR: c-m1-559dcf17d281e285b7f09f943b9706de.png<br>
c-m2-559dcf17d281e285b7f09f943b9706de.png  invalid sBIT length<br>
c-m2-559dcf17d281e285b7f09f943b9706de.png  PLTE not allowed in grayscale image<br>
c-m2-559dcf17d281e285b7f09f943b9706de.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m2-559dcf17d281e285b7f09f943b9706de.png<br>
m1-559dcf17d281e285b7f09f943b9706de.png  CRC error in chunk IHDR (computed ed8067bf, expected 9a875729)<br>
m1-559dcf17d281e285b7f09f943b9706de.png  CRC error in chunk tRNS (computed 425e370a, expected f4381a37)<br>
m1-559dcf17d281e285b7f09f943b9706de.png  invalid IDAT row-filter type (9)<br>
ERROR: m1-559dcf17d281e285b7f09f943b9706de.png<br>
m2-559dcf17d281e285b7f09f943b9706de.png  CRC error in chunk IHDR (computed 8832f8c7, expected 9a875729)<br>
m2-559dcf17d281e285b7f09f943b9706de.png  invalid sBIT length<br>
m2-559dcf17d281e285b7f09f943b9706de.png  PLTE not allowed in grayscale image<br>
m2-559dcf17d281e285b7f09f943b9706de.png  zlib: inflate error = -3 (data error)<br>
ERROR: m2-559dcf17d281e285b7f09f943b9706de.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>579294d4d8110fc64980dd72a5066780.png</h3>

<ul><li>Origin: <code>brokensuite:plte_too_many_entries_2.png</code></li></ul>

<h4>Notes</h4>

<pre><code>579294d4d8110fc64980dd72a5066780.png  invalid number of PLTE entries (257)<br>
ERROR: 579294d4d8110fc64980dd72a5066780.png<br>
<br>
</code></pre>
<h3>c-m1-585dd0ac594e8226c49ae7986b8f47d3.png</h3>

<h3>m1-585dd0ac594e8226c49ae7986b8f47d3.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-585dd0ac594e8226c49ae7986b8f47d3.png  invalid gAMA length<br>
c-m1-585dd0ac594e8226c49ae7986b8f47d3.png  zlib: inflate error = -3 (data error)<br>
c-m1-585dd0ac594e8226c49ae7986b8f47d3.png  illegal reserved-bit-set chunk IEmD<br>
ERROR: c-m1-585dd0ac594e8226c49ae7986b8f47d3.png<br>
m1-585dd0ac594e8226c49ae7986b8f47d3.png  CRC error in chunk IHDR (computed d0f6e06c, expected 498bc8ef)<br>
m1-585dd0ac594e8226c49ae7986b8f47d3.png  invalid gAMA length<br>
m1-585dd0ac594e8226c49ae7986b8f47d3.png  zlib: inflate error = -3 (data error)<br>
m1-585dd0ac594e8226c49ae7986b8f47d3.png  illegal reserved-bit-set chunk IEmD<br>
ERROR: m1-585dd0ac594e8226c49ae7986b8f47d3.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>586914b5d01d3889fb7bb5c44fe29771.png</h3>

<h3>c-586914b5d01d3889fb7bb5c44fe29771.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>586914b5d01d3889fb7bb5c44fe29771.png  CRC error in chunk bKGD (computed dfe780ae, expected 1f5dec03)<br>
586914b5d01d3889fb7bb5c44fe29771.png  zlib: inflate error = -3 (data error)<br>
ERROR: 586914b5d01d3889fb7bb5c44fe29771.png<br>
c-586914b5d01d3889fb7bb5c44fe29771.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-586914b5d01d3889fb7bb5c44fe29771.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>c-m1-58d30745083f25952342caafb6ee5f37.png</h3>

<h3>m1-58d30745083f25952342caafb6ee5f37.png</h3>

<ul><li>Origin: <code>http://info.weather.yandex.net/informer/120x156/11120.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-58d30745083f25952342caafb6ee5f37.png  invalid IHDR image type (11)<br>
c-m1-58d30745083f25952342caafb6ee5f37.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-58d30745083f25952342caafb6ee5f37.png<br>
m1-58d30745083f25952342caafb6ee5f37.png  invalid IHDR image type (11)<br>
m1-58d30745083f25952342caafb6ee5f37.png  CRC error in chunk IHDR (computed 164b6bd8, expected e421b305)<br>
m1-58d30745083f25952342caafb6ee5f37.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-58d30745083f25952342caafb6ee5f37.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>c-m2-593d4b1a0b5d13b539c6c098dc5797ca.png</h3>

<h3>c-m3-593d4b1a0b5d13b539c6c098dc5797ca.png</h3>

<h3>m1-593d4b1a0b5d13b539c6c098dc5797ca.png</h3>

<h3>m2-593d4b1a0b5d13b539c6c098dc5797ca.png</h3>

<h3>m3-593d4b1a0b5d13b539c6c098dc5797ca.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m2-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m2-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (28)<br>
c-m2-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
c-m2-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (73)<br>
c-m2-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (121)<br>
ERROR: c-m2-593d4b1a0b5d13b539c6c098dc5797ca.png<br>
c-m3-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m3-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (28)<br>
c-m3-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
c-m3-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (73)<br>
c-m3-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (121)<br>
ERROR: c-m3-593d4b1a0b5d13b539c6c098dc5797ca.png<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png  first chunk must be IHDR<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png  illegal (unless recently approved) unknown, public chunk vHDR<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png  first chunk must be IHDR<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png:  invalid chunk name "IDA�" (49 44 41 ffffffaf)<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png  first chunk must be IHDR<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png  illegal critical, safe-to-copy chunk IDA�<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png  first chunk must be IHDR<br>
m1-593d4b1a0b5d13b539c6c098dc5797ca.png  no IDAT chunks<br>
ERROR: m1-593d4b1a0b5d13b539c6c098dc5797ca.png<br>
m2-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m2-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (28)<br>
m2-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
m2-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (73)<br>
m2-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (121)<br>
m2-593d4b1a0b5d13b539c6c098dc5797ca.png  CRC error in chunk IDAT (computed 4c13f9e8, expected 5542ce25)<br>
ERROR: m2-593d4b1a0b5d13b539c6c098dc5797ca.png<br>
m3-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m3-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (28)<br>
m3-593d4b1a0b5d13b539c6c098dc5797ca.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
m3-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (73)<br>
m3-593d4b1a0b5d13b539c6c098dc5797ca.png  invalid IDAT row-filter type (121)<br>
m3-593d4b1a0b5d13b539c6c098dc5797ca.png  CRC error in chunk IDAT (computed 0deb5053, expected 5542ce25)<br>
ERROR: m3-593d4b1a0b5d13b539c6c098dc5797ca.png<br>
Errors were detected in 5 of the 5 files tested.<br>
<br>
</code></pre>
<h3>m1-5ae377bebf643e2e53ba7038103e48c4.png</h3>

<ul><li>Origin: <code>http://upload.wikimedia.org/wikipedia/commons/thumb/3/33/Flag_of_rcnl.png/120px-Flag_of_rcnl.png</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-5ae377bebf643e2e53ba7038103e48c4.png  private (invalid?) IDAT row-filter type (185) (warning)<br>
m1-5ae377bebf643e2e53ba7038103e48c4.png  invalid IDAT row-filter type (9)<br>
m1-5ae377bebf643e2e53ba7038103e48c4.png  zlib: inflate error = -3 (data error)<br>
m1-5ae377bebf643e2e53ba7038103e48c4.png  illegal (unless recently approved) unknown, public chunk sTXt<br>
ERROR: m1-5ae377bebf643e2e53ba7038103e48c4.png<br>
<br>
</code></pre>
<h3>5b689479bd7e527c2385a40437272607.png</h3>

<ul><li>Origin: <code>brokensuite:srgb_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>5b689479bd7e527c2385a40437272607.png  sRGB must precede IDAT<br>
ERROR: 5b689479bd7e527c2385a40437272607.png<br>
<br>
</code></pre>
<h3>5beaadc10dfdbf61124e98fdf8a5c191.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_ster.png</code></li></ul>

<h4>Notes</h4>

<pre><code>5beaadc10dfdbf61124e98fdf8a5c191.png  multiple sTER not allowed<br>
ERROR: 5beaadc10dfdbf61124e98fdf8a5c191.png<br>
<br>
</code></pre>
<h3>c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png</h3>

<h3>m1-5e149c14dc7b7c16ff6bcedd1625ca31.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (7)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (247) (warning)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (246) (warning)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (10)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (13)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (9)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (5)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (6)<br>
c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-5e149c14dc7b7c16ff6bcedd1625ca31.png<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (7)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  CRC error in chunk IDAT (computed 20dc9f00, expected a964ee42)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (247) (warning)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (246) (warning)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (10)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  CRC error in chunk IDAT (computed e4361d93, expected b9144328)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (13)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (9)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (5)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  invalid IDAT row-filter type (6)<br>
m1-5e149c14dc7b7c16ff6bcedd1625ca31.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-5e149c14dc7b7c16ff6bcedd1625ca31.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>5e2b64196b9e014e0ed0a27873cafdb3.png</h3>

<h3>c-5e2b64196b9e014e0ed0a27873cafdb3.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>5e2b64196b9e014e0ed0a27873cafdb3.png  sRGB invalid rendering intent<br>
5e2b64196b9e014e0ed0a27873cafdb3.png  CRC error in chunk sRGB (computed a9a3d8f0, expected aece1ce9)<br>
5e2b64196b9e014e0ed0a27873cafdb3.png  invalid cHRM red point 168.412 0.33<br>
5e2b64196b9e014e0ed0a27873cafdb3.png  CRC error in chunk cHRM (computed 1d9f341b, expected 9cba513c)<br>
ERROR: 5e2b64196b9e014e0ed0a27873cafdb3.png<br>
c-5e2b64196b9e014e0ed0a27873cafdb3.png  sRGB invalid rendering intent<br>
c-5e2b64196b9e014e0ed0a27873cafdb3.png  invalid cHRM red point 168.412 0.33<br>
ERROR: c-5e2b64196b9e014e0ed0a27873cafdb3.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>m1-5efba06832cc674ae5d290ba7ebc2533.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>611b294df9cf794eeaa1ffcc620bf6a4.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_offs.png</code></li></ul>

<h4>Notes</h4>

<pre><code>611b294df9cf794eeaa1ffcc620bf6a4.png  multiple oFFs not allowed<br>
ERROR: 611b294df9cf794eeaa1ffcc620bf6a4.png<br>
<br>
</code></pre>
<h3>6399623892b45aa4901aa6e702c7a62d.png</h3>

<ul><li>Origin: <code>brokensuite:scal_negative.png</code></li></ul>

<h4>Notes</h4>

<pre><code>6399623892b45aa4901aa6e702c7a62d.png  invalid negative sCAL value(s)<br>
ERROR: 6399623892b45aa4901aa6e702c7a62d.png<br>
<br>
</code></pre>
<h3>64221ffc9050c92b8980326acc0e4194.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_pcal.png</code></li></ul>

<h4>Notes</h4>

<pre><code>64221ffc9050c92b8980326acc0e4194.png  multiple pCAL not allowed<br>
ERROR: 64221ffc9050c92b8980326acc0e4194.png<br>
<br>
</code></pre>
<h3>c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png</h3>

<h3>m1-6593e140dba21ccb8c8724f8fe88fdb6.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (37)<br>
c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png  private (invalid?) IDAT row-filter type (181) (warning)<br>
c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (12)<br>
c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (100)<br>
c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (98)<br>
c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png  zlib: inflate error = -3 (data error)<br>
c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png  private (possibly invalid) zTXt compression method (132) (warning)<br>
ERROR: c-m1-6593e140dba21ccb8c8724f8fe88fdb6.png<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  CRC error in chunk IHDR (computed 8cd29595, expected 3c0171e2)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (37)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  private (invalid?) IDAT row-filter type (181) (warning)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (12)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (100)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  CRC error in chunk IDAT (computed ad821b9e, expected ebadb2b8)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  invalid IDAT row-filter type (98)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  zlib: inflate error = -3 (data error)<br>
m1-6593e140dba21ccb8c8724f8fe88fdb6.png  private (possibly invalid) zTXt compression method (132) (warning)<br>
ERROR: m1-6593e140dba21ccb8c8724f8fe88fdb6.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>66ac49ef3f48ac9482049e1ab57a53e9.png</h3>

<h3>c-m1-66ac49ef3f48ac9482049e1ab57a53e9.png</h3>

<h3>c-m2-66ac49ef3f48ac9482049e1ab57a53e9.png</h3>

<h3>c-m3-66ac49ef3f48ac9482049e1ab57a53e9.png</h3>

<h3>m1-66ac49ef3f48ac9482049e1ab57a53e9.png</h3>

<h3>m2-66ac49ef3f48ac9482049e1ab57a53e9.png</h3>

<h3>m3-66ac49ef3f48ac9482049e1ab57a53e9.png</h3>

<ul><li>Origin: <code>http://i17.photobucket.com/albums/b76/icedlain/ubuntu.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: 66ac49ef3f48ac9482049e1ab57a53e9.png (80x15, 32-bit RGB+alpha, non-interlaced, 16.0%).<br>
OK: c-m1-66ac49ef3f48ac9482049e1ab57a53e9.png (80x15, 32-bit RGB+alpha, non-interlaced, 16.0%).<br>
c-m2-66ac49ef3f48ac9482049e1ab57a53e9.png  zlib: inflate error = -3 (data error)<br>
c-m2-66ac49ef3f48ac9482049e1ab57a53e9.png  illegal critical, safe-to-copy chunk WTXt<br>
ERROR: c-m2-66ac49ef3f48ac9482049e1ab57a53e9.png<br>
OK: c-m3-66ac49ef3f48ac9482049e1ab57a53e9.png (80x15, 32-bit RGB+alpha, non-interlaced, 16.0%).<br>
m1-66ac49ef3f48ac9482049e1ab57a53e9.png  CRC error in chunk gAMA (computed f41078d0, expected 0bfc6105)<br>
m1-66ac49ef3f48ac9482049e1ab57a53e9.png  CRC error in chunk zTXt (computed 565f2318, expected bb0815b0)<br>
ERROR: m1-66ac49ef3f48ac9482049e1ab57a53e9.png<br>
m2-66ac49ef3f48ac9482049e1ab57a53e9.png  CRC error in chunk zTXt (computed 1d9c9e15, expected bb0815b0)<br>
m2-66ac49ef3f48ac9482049e1ab57a53e9.png  zlib: inflate error = -3 (data error)<br>
m2-66ac49ef3f48ac9482049e1ab57a53e9.png  illegal critical, safe-to-copy chunk WTXt<br>
ERROR: m2-66ac49ef3f48ac9482049e1ab57a53e9.png<br>
m3-66ac49ef3f48ac9482049e1ab57a53e9.png  CRC error in chunk zTXt (computed f6421cb4, expected bb0815b0)<br>
ERROR: m3-66ac49ef3f48ac9482049e1ab57a53e9.png<br>
Errors were detected in 4 of the 7 files tested.<br>
No errors were detected in 3 of the 7 files tested.<br>
<br>
</code></pre>
<h3>c-m1-6bfb149151f58d124d6fa76eaad75520.png</h3>

<h3>c-m4-6bfb149151f58d124d6fa76eaad75520.png</h3>

<h3>m1-6bfb149151f58d124d6fa76eaad75520.png</h3>

<h3>m2-6bfb149151f58d124d6fa76eaad75520.png</h3>

<h3>m3-6bfb149151f58d124d6fa76eaad75520.png</h3>

<h3>m4-6bfb149151f58d124d6fa76eaad75520.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-6bfb149151f58d124d6fa76eaad75520.png  PLTE not allowed in grayscale image<br>
ERROR: c-m1-6bfb149151f58d124d6fa76eaad75520.png<br>
OK: c-m4-6bfb149151f58d124d6fa76eaad75520.png (16x16, 1-bit palette, non-interlaced, -750.0%).<br>
m1-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk IHDR (computed 3788c2cc, expected 254b4f22)<br>
m1-6bfb149151f58d124d6fa76eaad75520.png  PLTE not allowed in grayscale image<br>
m1-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk IDAT (computed 165f63a5, expected 3faa858e)<br>
m1-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk tEXt (computed 344d4d5b, expected dc930890)<br>
m1-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk tEXt (computed 3a7a44ce, expected 83227ea4)<br>
m1-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk IEND (computed ae426082, expected ae8d6082)<br>
ERROR: m1-6bfb149151f58d124d6fa76eaad75520.png<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  illegal (unless recently approved) unknown, public chunk oHDR<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  illegal reserved-bit-set chunk ubzC<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  illegal (unless recently approved) unknown, public chunk mLTE<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m2-6bfb149151f58d124d6fa76eaad75520.png:  invalid chunk name "-07T" (2d 30 37 54)<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m2-6bfb149151f58d124d6fa76eaad75520.png  EOF while reading -07T data<br>
ERROR: m2-6bfb149151f58d124d6fa76eaad75520.png<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  illegal (unless recently approved) unknown, public chunk tHDR<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  illegal reserved-bit-set chunk ubzC<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  PLTE not allowed in INVALID image<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  first chunk must be IHDR<br>
m3-6bfb149151f58d124d6fa76eaad75520.png  EOF while reading pHYs data<br>
ERROR: m3-6bfb149151f58d124d6fa76eaad75520.png<br>
m4-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk IHDR (computed 253d6d22, expected 253d4f22)<br>
m4-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk tEXt (computed 344d4d5b, expected dc930890)<br>
m4-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk tEXt (computed 3ff9cdcd, expected 83227ea4)<br>
m4-6bfb149151f58d124d6fa76eaad75520.png  CRC error in chunk IEND (computed ae426082, expected ae8d6082)<br>
ERROR: m4-6bfb149151f58d124d6fa76eaad75520.png<br>
Errors were detected in 5 of the 6 files tested.<br>
No errors were detected in 1 of the 6 files tested.<br>
<br>
</code></pre>
<h3>6c853ed9dacd5716bc54eb59cec30889.png</h3>

<ul><li>Origin: <code>http://i187.photobucket.com/albums/x34/lcjhfrank/BLOG/04fang230.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: 6c853ed9dacd5716bc54eb59cec30889.png (724x1024, 48-bit RGB, non-interlaced, 35.6%).<br>
<br>
</code></pre>
<h3>c-m1-6e3914f26bcc8f9d004ffeac71656c01.png</h3>

<h3>m1-6e3914f26bcc8f9d004ffeac71656c01.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-6e3914f26bcc8f9d004ffeac71656c01.png  bKGD index (17) falls outside PLTE (16)<br>
c-m1-6e3914f26bcc8f9d004ffeac71656c01.png  private (invalid?) IDAT row-filter type (136) (warning)<br>
c-m1-6e3914f26bcc8f9d004ffeac71656c01.png  private (invalid?) IDAT row-filter type (238) (warning)<br>
ERROR: c-m1-6e3914f26bcc8f9d004ffeac71656c01.png<br>
m1-6e3914f26bcc8f9d004ffeac71656c01.png  CRC error in chunk IHDR (computed 1610b7ef, expected 61178779)<br>
m1-6e3914f26bcc8f9d004ffeac71656c01.png  bKGD index (17) falls outside PLTE (16)<br>
m1-6e3914f26bcc8f9d004ffeac71656c01.png  private (invalid?) IDAT row-filter type (136) (warning)<br>
m1-6e3914f26bcc8f9d004ffeac71656c01.png  private (invalid?) IDAT row-filter type (238) (warning)<br>
ERROR: m1-6e3914f26bcc8f9d004ffeac71656c01.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>71714b783e01aec455b5a4a760326ccc.png</h3>

<ul><li>Origin: <code>brokensuite:iccp_after_plte.png</code></li></ul>

<h4>Notes</h4>

<pre><code>71714b783e01aec455b5a4a760326ccc.png  iCCP must precede PLTE<br>
ERROR: 71714b783e01aec455b5a4a760326ccc.png<br>
<br>
</code></pre>
<h3>c-m2-71915ab0b1cc7350091ef7073a312d16.png</h3>

<h3>m1-71915ab0b1cc7350091ef7073a312d16.png</h3>

<h3>m2-71915ab0b1cc7350091ef7073a312d16.png</h3>

<h3>m3-71915ab0b1cc7350091ef7073a312d16.png</h3>

<ul><li>Origin: <code>http://upload.wikimedia.org/wikipedia/commons/thumb/0/09/European_Parliament_6th_term_new.png/60px-European_Parliament_6th_term_new.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m2-71915ab0b1cc7350091ef7073a312d16.png  zlib: inflate error = -3 (data error)<br>
c-m2-71915ab0b1cc7350091ef7073a312d16.png  zTXt keyword has control character(s) (138)<br>
ERROR: c-m2-71915ab0b1cc7350091ef7073a312d16.png<br>
m1-71915ab0b1cc7350091ef7073a312d16.png  first chunk must be IHDR<br>
m1-71915ab0b1cc7350091ef7073a312d16.png  illegal (unless recently approved) unknown, public chunk vHDR<br>
m1-71915ab0b1cc7350091ef7073a312d16.png  first chunk must be IHDR<br>
m1-71915ab0b1cc7350091ef7073a312d16.png  invalid zTXt compression method (99)<br>
m1-71915ab0b1cc7350091ef7073a312d16.png  first chunk must be IHDR<br>
m1-71915ab0b1cc7350091ef7073a312d16.png  EOF while reading ight data<br>
ERROR: m1-71915ab0b1cc7350091ef7073a312d16.png<br>
m2-71915ab0b1cc7350091ef7073a312d16.png  CRC error in chunk cHRM (computed 9cba513c, expected 9cba51d3)<br>
m2-71915ab0b1cc7350091ef7073a312d16.png  CRC error in chunk vpAg (computed c1d83cff, expected c1d83c27)<br>
m2-71915ab0b1cc7350091ef7073a312d16.png  zlib: inflate error = -3 (data error)<br>
m2-71915ab0b1cc7350091ef7073a312d16.png  zTXt keyword has control character(s) (138)<br>
ERROR: m2-71915ab0b1cc7350091ef7073a312d16.png<br>
m3-71915ab0b1cc7350091ef7073a312d16.png  illegal reserved-bit-set chunk gAhA<br>
m3-71915ab0b1cc7350091ef7073a312d16.png  zlib: inflate error = -3 (data error)<br>
m3-71915ab0b1cc7350091ef7073a312d16.png  zTXt keyword has control character(s) (138)<br>
ERROR: m3-71915ab0b1cc7350091ef7073a312d16.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>71dd006377602359ebd2cbe7b9eaab09.png</h3>

<h3>c-71dd006377602359ebd2cbe7b9eaab09.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>71dd006377602359ebd2cbe7b9eaab09.png  invalid IHDR sample depth (4) for RGB+alpha image<br>
71dd006377602359ebd2cbe7b9eaab09.png  CRC error in chunk IHDR (computed b797a415, expected 498b65ef)<br>
71dd006377602359ebd2cbe7b9eaab09.png  CRC error in chunk gAMA (computed 37058ae9, expected 3705cfe9)<br>
71dd006377602359ebd2cbe7b9eaab09.png  CRC error in chunk tEXt (computed a0b8acd2, expected 66747761)<br>
71dd006377602359ebd2cbe7b9eaab09.png  EOF while reading dobe data<br>
ERROR: 71dd006377602359ebd2cbe7b9eaab09.png<br>
c-71dd006377602359ebd2cbe7b9eaab09.png  invalid IHDR sample depth (4) for RGB+alpha image<br>
c-71dd006377602359ebd2cbe7b9eaab09.png  EOF while reading dobe data<br>
ERROR: c-71dd006377602359ebd2cbe7b9eaab09.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>743b8442c69efbc457af7376af71b44c.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>743b8442c69efbc457af7376af71b44c.png  first chunk must be IHDR<br>
743b8442c69efbc457af7376af71b44c.png  illegal (unless recently approved) unknown, public chunk aHDR<br>
743b8442c69efbc457af7376af71b44c.png  first chunk must be IHDR<br>
743b8442c69efbc457af7376af71b44c.png  invalid bKGD length<br>
743b8442c69efbc457af7376af71b44c.png  first chunk must be IHDR<br>
ERROR: 743b8442c69efbc457af7376af71b44c.png<br>
<br>
</code></pre>
<h3>7b9abb94ace0278f943a6df29d0ca652.png</h3>

<ul><li>Origin: <code>brokensuite:gama_after_plte.png</code></li></ul>

<h4>Notes</h4>

<pre><code>7b9abb94ace0278f943a6df29d0ca652.png  gAMA must precede PLTE<br>
ERROR: 7b9abb94ace0278f943a6df29d0ca652.png<br>
<br>
</code></pre>
<h3>7ce702ec69b7af26b3218d1278520bce.png</h3>

<ul><li>Origin: <code>brokensuite:private_filter_method.png</code></li></ul>

<h4>Notes</h4>

<pre><code>7ce702ec69b7af26b3218d1278520bce.png  private (invalid?) IHDR filter method (128) (warning)<br>
WARN: 7ce702ec69b7af26b3218d1278520bce.png (32x32, 8-bit palette, non-interlaced, -25.6%).<br>
<br>
</code></pre>
<h3>m1-7dc9db3d3e510156c619273f8f913cbe.png</h3>

<ul><li>Origin: <code>http://www.wseip.edu.pl/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.bcmalta.com/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.tt-rotamsee.de/nw14/pics/printButton.png</code>
</li><li>Origin: <code>http://flokkarinn.is/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://web.utm.my/wangi/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.sbmicro.org.br/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.keginvestments.com//images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.vccn.nl/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.coddington.org.uk/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://space.globehosting.net/~beliu1/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://tssi.no/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.fragielex.nl/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://gold-elites.com.ua/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.fisherclub.com.ua/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.cyberinfo.undip.ac.id/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.fuu.de/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.dance.is/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.deltacad-portugal.com/main/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.networkimprese.it/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.nightspot.at/templates/fotos/images/printButton.png</code>
</li><li>Origin: <code>http://www.vogelopvangcentrum-malderen.be/images/M_images/printButton.png</code>
</li><li>Origin: <code>http://www.thw-obernburg.de/news/pics/printButton.png</code>
</li><li>Origin: <code>http://www.il2mania.com/images/M_images/printButton.png</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-7dc9db3d3e510156c619273f8f913cbe.png  illegal (unless recently approved) unknown, public chunk vLTE<br>
m1-7dc9db3d3e510156c619273f8f913cbe.png  EOF while reading tRNS data<br>
ERROR: m1-7dc9db3d3e510156c619273f8f913cbe.png<br>
<br>
</code></pre>
<h3>c-m1-80e163ebface8b0d2fbf9823bca02936.png</h3>

<h3>c-m2-80e163ebface8b0d2fbf9823bca02936.png</h3>

<h3>m1-80e163ebface8b0d2fbf9823bca02936.png</h3>

<h3>m2-80e163ebface8b0d2fbf9823bca02936.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-80e163ebface8b0d2fbf9823bca02936.png  zlib: inflate error = -3 (data error)<br>
c-m1-80e163ebface8b0d2fbf9823bca02936.png  illegal (unless recently approved) unknown, public chunk kEND<br>
ERROR: c-m1-80e163ebface8b0d2fbf9823bca02936.png<br>
c-m2-80e163ebface8b0d2fbf9823bca02936.png  invalid cHRM green point 0.3 56.961<br>
c-m2-80e163ebface8b0d2fbf9823bca02936.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m2-80e163ebface8b0d2fbf9823bca02936.png<br>
m1-80e163ebface8b0d2fbf9823bca02936.png  CRC error in chunk pHYs (computed 78a53f76, expected 3aa53f76)<br>
m1-80e163ebface8b0d2fbf9823bca02936.png  zlib: inflate error = -3 (data error)<br>
m1-80e163ebface8b0d2fbf9823bca02936.png  illegal (unless recently approved) unknown, public chunk kEND<br>
ERROR: m1-80e163ebface8b0d2fbf9823bca02936.png<br>
m2-80e163ebface8b0d2fbf9823bca02936.png  CRC error in chunk iCCP (computed 32f48ee5, expected fa96f15d)<br>
m2-80e163ebface8b0d2fbf9823bca02936.png  invalid cHRM green point 0.3 56.961<br>
m2-80e163ebface8b0d2fbf9823bca02936.png  CRC error in chunk cHRM (computed 0254d221, expected 925fc546)<br>
m2-80e163ebface8b0d2fbf9823bca02936.png  zlib: inflate error = -3 (data error)<br>
ERROR: m2-80e163ebface8b0d2fbf9823bca02936.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>m1-814fcedc62fe4e43923c042ff1d6747f.png</h3>

<h3>m2-814fcedc62fe4e43923c042ff1d6747f.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-814fcedc62fe4e43923c042ff1d6747f.png  zlib: inflate error = -3 (data error)<br>
m1-814fcedc62fe4e43923c042ff1d6747f.png  tEXt keyword has control character(s) (10)<br>
ERROR: m1-814fcedc62fe4e43923c042ff1d6747f.png<br>
m2-814fcedc62fe4e43923c042ff1d6747f.png  first chunk must be IHDR<br>
m2-814fcedc62fe4e43923c042ff1d6747f.png  illegal (unless recently approved) unknown, public chunk vHDR<br>
m2-814fcedc62fe4e43923c042ff1d6747f.png  first chunk must be IHDR<br>
m2-814fcedc62fe4e43923c042ff1d6747f.png  invalid pHYs length<br>
m2-814fcedc62fe4e43923c042ff1d6747f.png  invalid chunk length (too large)<br>
ERROR: m2-814fcedc62fe4e43923c042ff1d6747f.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>817f96555e2d683e7b12f778c4e38022.png</h3>

<h3>c-817f96555e2d683e7b12f778c4e38022.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>817f96555e2d683e7b12f778c4e38022.png  CRC error in chunk IHDR (computed 06d4b8a8, expected 498b65ef)<br>
817f96555e2d683e7b12f778c4e38022.png  invalid gAMA length<br>
817f96555e2d683e7b12f778c4e38022.png:  invalid chunk name "�b��" (ffffffda 62 fffffffc ffffffff)<br>
817f96555e2d683e7b12f778c4e38022.png  EOF while reading �b�� data<br>
ERROR: 817f96555e2d683e7b12f778c4e38022.png<br>
c-817f96555e2d683e7b12f778c4e38022.png  invalid gAMA length<br>
c-817f96555e2d683e7b12f778c4e38022.png:  invalid chunk name "�b��" (ffffffda 62 fffffffc ffffffff)<br>
c-817f96555e2d683e7b12f778c4e38022.png  EOF while reading �b�� data<br>
ERROR: c-817f96555e2d683e7b12f778c4e38022.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>829b05b759b2977bc3eb970ab256d867.png</h3>

<ul><li>Origin: <code>brokensuite:iccp_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>829b05b759b2977bc3eb970ab256d867.png  iCCP must precede IDAT<br>
ERROR: 829b05b759b2977bc3eb970ab256d867.png<br>
<br>
</code></pre>
<h3>8711007ea5e351755a80cba913d16a32.png</h3>

<ul><li>Origin: <code>brokensuite:splt_length_mod_10.png</code></li></ul>

<h4>Notes</h4>

<pre><code>8711007ea5e351755a80cba913d16a32.png  invalid number of sPLT entries (0.6)<br>
ERROR: 8711007ea5e351755a80cba913d16a32.png<br>
<br>
</code></pre>
<h3>8905ba870cd5d3327a8310fa437aa076.png</h3>

<ul><li>Origin: <code>brokensuite:scal_floating_point.png</code></li></ul>

<h4>Notes</h4>

<pre><code>8905ba870cd5d3327a8310fa437aa076.png  invalid character ('Q' = 0x51) in sCAL<br>
ERROR: 8905ba870cd5d3327a8310fa437aa076.png<br>
<br>
</code></pre>
<h3>c-m1-8f2b481b7fd9bd745e620b7c01a18df2.png</h3>

<h3>c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png</h3>

<h3>m1-8f2b481b7fd9bd745e620b7c01a18df2.png</h3>

<h3>m2-8f2b481b7fd9bd745e620b7c01a18df2.png</h3>

<ul><li>Origin: <code>http://ibed-inst-de-gastroent-e-endosc-digestiv-ltda.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code>
</li><li>Origin: <code>http://centro-medico-sao-silvestre-s-c-ltda.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code>
</li><li>Origin: <code>http://amiu-casa-de-saude-e-assist-med-infantil-de-urg.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code>
</li><li>Origin: <code>http://kleber-gaspar-carvalho-da-silva.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code>
</li><li>Origin: <code>http://leticia-krause-schenato.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code>
</li><li>Origin: <code>http://ortopedistas-e-traumatologistas.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code>
</li><li>Origin: <code>http://conmedh-conv-med-hospitalares-clinica-sao-camilo.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code>
</li><li>Origin: <code>http://hgu-centro-hospitalar-sao-francisco.catalogo.med.br/_res/Element_hbPortal/Page_itn_mn_3.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-8f2b481b7fd9bd745e620b7c01a18df2.png  tEXt keyword is longer than 79 characters<br>
c-m1-8f2b481b7fd9bd745e620b7c01a18df2.png  illegal (unless recently approved) unknown, public chunk wEND<br>
ERROR: c-m1-8f2b481b7fd9bd745e620b7c01a18df2.png<br>
c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png  invalid sBIT length<br>
c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png  invalid pHYs unit specifier (186)<br>
c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png  tEXt text contains NULL character(s)<br>
c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png  private (invalid?) IDAT row-filter type (206) (warning)<br>
c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png  private (invalid?) IDAT row-filter type (212) (warning)<br>
c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png  private (invalid?) IDAT row-filter type (206) (warning)<br>
c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png  invalid IDAT row-filter type (40)<br>
ERROR: c-m2-8f2b481b7fd9bd745e620b7c01a18df2.png<br>
m1-8f2b481b7fd9bd745e620b7c01a18df2.png  tEXt keyword is longer than 79 characters<br>
m1-8f2b481b7fd9bd745e620b7c01a18df2.png  CRC error in chunk tEXt (computed 53f53b16, expected eede1190)<br>
m1-8f2b481b7fd9bd745e620b7c01a18df2.png  illegal (unless recently approved) unknown, public chunk wEND<br>
ERROR: m1-8f2b481b7fd9bd745e620b7c01a18df2.png<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  CRC error in chunk IHDR (computed 01ad28bd, expected 24c67761)<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  invalid sBIT length<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  invalid pHYs unit specifier (186)<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  tEXt text contains NULL character(s)<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  private (invalid?) IDAT row-filter type (206) (warning)<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  private (invalid?) IDAT row-filter type (212) (warning)<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  private (invalid?) IDAT row-filter type (206) (warning)<br>
m2-8f2b481b7fd9bd745e620b7c01a18df2.png  invalid IDAT row-filter type (40)<br>
ERROR: m2-8f2b481b7fd9bd745e620b7c01a18df2.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>9032e447e32e09aef5b7de2fab42494d.png</h3>

<h3>c-9032e447e32e09aef5b7de2fab42494d.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>9032e447e32e09aef5b7de2fab42494d.png  multiple IHDR not allowed<br>
9032e447e32e09aef5b7de2fab42494d.png  invalid IHDR image type (192)<br>
9032e447e32e09aef5b7de2fab42494d.png  invalid IHDR sample depth (126)<br>
9032e447e32e09aef5b7de2fab42494d.png  invalid IHDR compression method (96)<br>
9032e447e32e09aef5b7de2fab42494d.png  private (invalid?) IHDR filter method (199) (warning)<br>
9032e447e32e09aef5b7de2fab42494d.png  private (invalid?) IHDR interlace method (160) (warning)<br>
9032e447e32e09aef5b7de2fab42494d.png  CRC error in chunk IHDR (computed a8a1ae0a, expected ae426082)<br>
9032e447e32e09aef5b7de2fab42494d.png  file doesn't end with an IEND chunk<br>
ERROR: 9032e447e32e09aef5b7de2fab42494d.png<br>
c-9032e447e32e09aef5b7de2fab42494d.png  multiple IHDR not allowed<br>
c-9032e447e32e09aef5b7de2fab42494d.png  invalid IHDR image type (192)<br>
c-9032e447e32e09aef5b7de2fab42494d.png  invalid IHDR sample depth (126)<br>
c-9032e447e32e09aef5b7de2fab42494d.png  invalid IHDR compression method (96)<br>
c-9032e447e32e09aef5b7de2fab42494d.png  private (invalid?) IHDR filter method (199) (warning)<br>
c-9032e447e32e09aef5b7de2fab42494d.png  private (invalid?) IHDR interlace method (160) (warning)<br>
c-9032e447e32e09aef5b7de2fab42494d.png  file doesn't end with an IEND chunk<br>
ERROR: c-9032e447e32e09aef5b7de2fab42494d.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>93e6127b9c4e7a99459c558b81d31bc5.png</h3>

<ul><li>Origin: <code>http://a.deviantart.com/avatars/u/l/ultra-sex.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: 93e6127b9c4e7a99459c558b81d31bc5.png (50x50, 32-bit grayscale+alpha, interlaced, 54.1%).<br>
<br>
</code></pre>
<h3>94e1bdbb03c42581d8407602634636ea.png</h3>

<h3>c-94e1bdbb03c42581d8407602634636ea.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>94e1bdbb03c42581d8407602634636ea.png  sPLT must precede IDAT<br>
94e1bdbb03c42581d8407602634636ea.png  CRC error in chunk sPLT (computed 04b86b3a, expected ae426082)<br>
94e1bdbb03c42581d8407602634636ea.png  file doesn't end with an IEND chunk<br>
ERROR: 94e1bdbb03c42581d8407602634636ea.png<br>
c-94e1bdbb03c42581d8407602634636ea.png  sPLT must precede IDAT<br>
c-94e1bdbb03c42581d8407602634636ea.png  file doesn't end with an IEND chunk<br>
ERROR: c-94e1bdbb03c42581d8407602634636ea.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>m1-94f94e608d647b1b433f4d0ecc21e023.png</h3>

<h3>m2-94f94e608d647b1b433f4d0ecc21e023.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>9540743374e1fdb273b6a6ca625eb7a3.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>9540743374e1fdb273b6a6ca625eb7a3.png  invalid gAMA value (0.0000)<br>
9540743374e1fdb273b6a6ca625eb7a3.png  invalid cHRM white point 42949.7 42949.7<br>
ERROR: 9540743374e1fdb273b6a6ca625eb7a3.png<br>
<br>
</code></pre>
<h3>c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png</h3>

<h3>c-m4-96b70653ba3f8a83b7cfd48749bed8b1.png</h3>

<h3>m1-96b70653ba3f8a83b7cfd48749bed8b1.png</h3>

<h3>m2-96b70653ba3f8a83b7cfd48749bed8b1.png</h3>

<h3>m3-96b70653ba3f8a83b7cfd48749bed8b1.png</h3>

<h3>m4-96b70653ba3f8a83b7cfd48749bed8b1.png</h3>

<ul><li>Origin: <code>http://www-em.materials.ox.ac.uk/photos/AntalKoos.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  iCCP not allowed with sRGB<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (243) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (252) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (248) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (252) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (253) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (5)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (252) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (252) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (248) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (238) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (248) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (243) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (252) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (6)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (231) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (14)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (5)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (11)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (10)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (245) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (236) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (24)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (8)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (249) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (239) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (7)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (10)<br>
c-m2-96b70653ba3f8a83b7cfd48749bed8b1.png  invalid IDAT row-filter type (6)<br>
c-m2-96b70653ba3f<br>
<br>
</code></pre>
<h3>9a3e0c7b687b526987e2270541002d47.png</h3>

<h3>c-9a3e0c7b687b526987e2270541002d47.png</h3>

<h3>c-m1-9a3e0c7b687b526987e2270541002d47.png</h3>

<h3>c-m2-9a3e0c7b687b526987e2270541002d47.png</h3>

<h3>m1-9a3e0c7b687b526987e2270541002d47.png</h3>

<h3>m2-9a3e0c7b687b526987e2270541002d47.png</h3>

<h3>m3-9a3e0c7b687b526987e2270541002d47.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>9a3e0c7b687b526987e2270541002d47.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
9a3e0c7b687b526987e2270541002d47.png  invalid IDAT row-filter type (21)<br>
9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk IDAT (computed 1c41dcde, expected 81be9b02)<br>
9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk zTXt (computed a6ccd434, expected 98310798)<br>
9a3e0c7b687b526987e2270541002d47.png  invalid zTXt compression method (120)<br>
9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk zTXt (computed 5fc2f3c2, expected 5f3947e2)<br>
9a3e0c7b687b526987e2270541002d47.png  illegal reserved-bit-set chunk zTot<br>
9a3e0c7b687b526987e2270541002d47.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
ERROR: 9a3e0c7b687b526987e2270541002d47.png<br>
c-9a3e0c7b687b526987e2270541002d47.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-9a3e0c7b687b526987e2270541002d47.png  invalid IDAT row-filter type (21)<br>
c-9a3e0c7b687b526987e2270541002d47.png  invalid zTXt compression method (120)<br>
c-9a3e0c7b687b526987e2270541002d47.png  illegal reserved-bit-set chunk zTot<br>
c-9a3e0c7b687b526987e2270541002d47.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
ERROR: c-9a3e0c7b687b526987e2270541002d47.png<br>
c-m1-9a3e0c7b687b526987e2270541002d47.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-9a3e0c7b687b526987e2270541002d47.png  invalid IDAT row-filter type (22)<br>
c-m1-9a3e0c7b687b526987e2270541002d47.png  illegal reserved-bit-set chunk zTlt<br>
c-m1-9a3e0c7b687b526987e2270541002d47.png  invalid zTXt compression method (58)<br>
c-m1-9a3e0c7b687b526987e2270541002d47.png:  invalid chunk name "pe�" (70 65 ffffffc1 00)<br>
c-m1-9a3e0c7b687b526987e2270541002d47.png  EOF while reading pe� data<br>
ERROR: c-m1-9a3e0c7b687b526987e2270541002d47.png<br>
c-m2-9a3e0c7b687b526987e2270541002d47.png  private (invalid?) IDAT row-filter type (190) (warning)<br>
c-m2-9a3e0c7b687b526987e2270541002d47.png  invalid IDAT row-filter type (40)<br>
c-m2-9a3e0c7b687b526987e2270541002d47.png  invalid zTXt compression method (120)<br>
c-m2-9a3e0c7b687b526987e2270541002d47.png  illegal reserved-bit-set chunk zTot<br>
c-m2-9a3e0c7b687b526987e2270541002d47.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
c-m2-9a3e0c7b687b526987e2270541002d47.png  EOF while reading IEND data<br>
ERROR: c-m2-9a3e0c7b687b526987e2270541002d47.png<br>
m1-9a3e0c7b687b526987e2270541002d47.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-9a3e0c7b687b526987e2270541002d47.png  invalid IDAT row-filter type (22)<br>
m1-9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk IDAT (computed 859e8018, expected 81be9b02)<br>
m1-9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk zTXt (computed 7ae72cac, expected 98310798)<br>
m1-9a3e0c7b687b526987e2270541002d47.png  illegal reserved-bit-set chunk zTlt<br>
m1-9a3e0c7b687b526987e2270541002d47.png  invalid zTXt compression method (58)<br>
m1-9a3e0c7b687b526987e2270541002d47.png:  invalid chunk name "pe�" (70 65 ffffffc1 00)<br>
m1-9a3e0c7b687b526987e2270541002d47.png  EOF while reading pe� data<br>
ERROR: m1-9a3e0c7b687b526987e2270541002d47.png<br>
m2-9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk IHDR (computed 6860fccf, expected 1f67cc59)<br>
m2-9a3e0c7b687b526987e2270541002d47.png  private (invalid?) IDAT row-filter type (190) (warning)<br>
m2-9a3e0c7b687b526987e2270541002d47.png  invalid IDAT row-filter type (40)<br>
m2-9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk IDAT (computed 79a48244, expected 81be9b02)<br>
m2-9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk zTXt (computed 45f6d3b9, expected 98310798)<br>
m2-9a3e0c7b687b526987e2270541002d47.png  invalid zTXt compression method (120)<br>
m2-9a3e0c7b687b526987e2270541002d47.png  CRC error in chunk zTXt (computed 5fc2f3c2, expected 5f3947e2)<br>
m2-9a3e0c7b687b526987e2270541002d47.png  illegal reserved-bit-set chunk zTot<br>
m2-9a3e0c7b687b526987e2270541002d47.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
m2-9a3e0c7b687b526987e2270541002d47.png  EOF while reading IEND data<br>
ERROR: m2-9a3e0c7b687b526987e2270541002d47.png<br>
m3-9a3e0c7b687b526987e2270541002d47.png  illegal (unless recently approved) unknown, public chunk uDAT<br>
m3-9a3e0c7b687b526987e2270541002d47.png  invalid zTXt compression method (120)<br>
m3-9a3e0c7b687b526987e2270541002d47.png  illegal reserved-bit-set chunk zTot<br>
m3-9a3e0c7b687b526987e2270541002d47.png  illegal (unless recently approved) unknown, public chunk zTXE<br>
m3-9a3e0c7b687b526987e2270541002d47.png  no IDAT chunks<br>
ERROR: m3-9a3e0c7b687b526987e2270541002d47.png<br>
Errors were detected in 7 of the 7 files tested.<br>
<br>
</code></pre>
<h3>9bd8a9ed81c5a9190f74496197da7249.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_time.png</code></li></ul>

<h4>Notes</h4>

<pre><code>9bd8a9ed81c5a9190f74496197da7249.png  multiple tIME not allowed<br>
ERROR: 9bd8a9ed81c5a9190f74496197da7249.png<br>
<br>
</code></pre>
<h3>m1-9bec9d0461c0ef0f5faf16d0d4bdcc13.png</h3>

<ul><li>Origin: <code>http://img237.imageshack.us/img237/4148/verrohhhhla5.png</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>m1-9eb5b67f01da30f0e16062004c343e4a.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-9eb5b67f01da30f0e16062004c343e4a.png  invalid tRNS length for RGB image<br>
m1-9eb5b67f01da30f0e16062004c343e4a.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-9eb5b67f01da30f0e16062004c343e4a.png<br>
<br>
</code></pre>
<h3>a1d1aafb5bca660229f8e9fc65291eab.png</h3>

<ul><li>Origin: <code>brokensuite:private_compression_method.png</code></li></ul>

<h4>Notes</h4>

<pre><code>a1d1aafb5bca660229f8e9fc65291eab.png  private (invalid?) IHDR compression method (128) (warning)<br>
WARN: a1d1aafb5bca660229f8e9fc65291eab.png (32x32, 8-bit palette, non-interlaced, -25.6%).<br>
<br>
</code></pre>
<h3>a1d54c960686558901e320a52a967158.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_hist.png</code></li></ul>

<h4>Notes</h4>

<pre><code>a1d54c960686558901e320a52a967158.png  multiple hIST not allowed<br>
ERROR: a1d54c960686558901e320a52a967158.png<br>
<br>
</code></pre>
<h3>c-m2-a1f9d85a8243b884d40e74f656c55e75.png</h3>

<h3>m1-a1f9d85a8243b884d40e74f656c55e75.png</h3>

<h3>m2-a1f9d85a8243b884d40e74f656c55e75.png</h3>

<ul><li>Origin: <code>http://cgi.members.interq.or.jp/blues/zetigoya/image/sd_em19.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m2-a1f9d85a8243b884d40e74f656c55e75.png  invalid IDAT row-filter type (17)<br>
c-m2-a1f9d85a8243b884d40e74f656c55e75.png  illegal (unless recently approved) unknown, public chunk tEND<br>
ERROR: c-m2-a1f9d85a8243b884d40e74f656c55e75.png<br>
m1-a1f9d85a8243b884d40e74f656c55e75.png  illegal (unless recently approved) unknown, public chunk uLTE<br>
m1-a1f9d85a8243b884d40e74f656c55e75.png  tRNS must follow PLTE<br>
m1-a1f9d85a8243b884d40e74f656c55e75.png:  invalid chunk name "tEX" (15 74 45 58)<br>
m1-a1f9d85a8243b884d40e74f656c55e75.png  EOF while reading tEX data<br>
ERROR: m1-a1f9d85a8243b884d40e74f656c55e75.png<br>
m2-a1f9d85a8243b884d40e74f656c55e75.png  CRC error in chunk IHDR (computed 19d6d7a7, expected 6ed1e731)<br>
m2-a1f9d85a8243b884d40e74f656c55e75.png  CRC error in chunk tEXt (computed be818c22, expected 8a6acd3f)<br>
m2-a1f9d85a8243b884d40e74f656c55e75.png  invalid IDAT row-filter type (17)<br>
m2-a1f9d85a8243b884d40e74f656c55e75.png  CRC error in chunk IDAT (computed 4bd3cd55, expected a01f3816)<br>
m2-a1f9d85a8243b884d40e74f656c55e75.png  illegal (unless recently approved) unknown, public chunk tEND<br>
ERROR: m2-a1f9d85a8243b884d40e74f656c55e75.png<br>
Errors were detected in 3 of the 3 files tested.<br>
<br>
</code></pre>
<h3>a24a39e69554a701412b3ed0c009e7f6.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_chrm.png</code></li></ul>

<h4>Notes</h4>

<pre><code>a24a39e69554a701412b3ed0c009e7f6.png  multiple cHRM not allowed<br>
ERROR: a24a39e69554a701412b3ed0c009e7f6.png<br>
<br>
</code></pre>
<h3>c-m2-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>c-m3-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>c-m4-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>c-m5-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>c-m6-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>c-m7-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>c-m8-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m1-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m2-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m3-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m4-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m5-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m6-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m7-a46ce91d8975a017917156b8824f936e.png</h3>

<h3>m8-a46ce91d8975a017917156b8824f936e.png</h3>

<ul><li>Origin: <code>http://www.dif.pref.tochigi.lg.jp/images/index0823.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m2-a46ce91d8975a017917156b8824f936e.png  invalid cHRM white point 0.31269 103.221<br>
c-m2-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 1-bit image<br>
c-m2-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m2-a46ce91d8975a017917156b8824f936e.png<br>
c-m3-a46ce91d8975a017917156b8824f936e.png  invalid cHRM white point 0.31269 8724.48<br>
c-m3-a46ce91d8975a017917156b8824f936e.png  illegal (unless recently approved) unknown, public chunk jLTE<br>
c-m3-a46ce91d8975a017917156b8824f936e.png  IDAT must follow PLTE in palette image<br>
c-m3-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m3-a46ce91d8975a017917156b8824f936e.png<br>
c-m4-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (293)<br>
c-m4-a46ce91d8975a017917156b8824f936e.png:  invalid chunk name "m�&lt;%" (6d ffffffc0 3c 25)<br>
c-m4-a46ce91d8975a017917156b8824f936e.png  EOF while reading m�&lt;% data<br>
ERROR: c-m4-a46ce91d8975a017917156b8824f936e.png<br>
c-m5-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk cHRM (computed 925fc546, expected 925f0a46)<br>
c-m5-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 1-bit image<br>
c-m5-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
c-m5-a46ce91d8975a017917156b8824f936e.png  illegal (unless recently approved) unknown, public chunk IQND<br>
ERROR: c-m5-a46ce91d8975a017917156b8824f936e.png<br>
c-m6-a46ce91d8975a017917156b8824f936e.png  invalid tIME hour (57)<br>
c-m6-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = 2 (unknown)<br>
ERROR: c-m6-a46ce91d8975a017917156b8824f936e.png<br>
c-m7-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 4-bit image<br>
c-m7-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
c-m7-a46ce91d8975a017917156b8824f936e.png  EOF while reading IEND data<br>
ERROR: c-m7-a46ce91d8975a017917156b8824f936e.png<br>
c-m8-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 2-bit image<br>
c-m8-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m8-a46ce91d8975a017917156b8824f936e.png<br>
m1-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-a46ce91d8975a017917156b8824f936e.png<br>
m2-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk IHDR (computed 74ad9407, expected 79bdf676)<br>
m2-a46ce91d8975a017917156b8824f936e.png  invalid cHRM white point 0.31269 103.221<br>
m2-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk cHRM (computed 9f5298f6, expected 925fc546)<br>
m2-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 1-bit image<br>
m2-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk PLTE (computed dce1e344, expected 30a7a68a)<br>
m2-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
ERROR: m2-a46ce91d8975a017917156b8824f936e.png<br>
m3-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk IHDR (computed bc4d1b77, expected 79bdf676)<br>
m3-a46ce91d8975a017917156b8824f936e.png  invalid cHRM white point 0.31269 8724.48<br>
m3-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk cHRM (computed b9684342, expected 925fc546)<br>
m3-a46ce91d8975a017917156b8824f936e.png  illegal (unless recently approved) unknown, public chunk jLTE<br>
m3-a46ce91d8975a017917156b8824f936e.png  IDAT must follow PLTE in palette image<br>
m3-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
ERROR: m3-a46ce91d8975a017917156b8824f936e.png<br>
m4-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (293)<br>
m4-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk PLTE (computed 702a2aba, expected 9c9d48a6)<br>
m4-a46ce91d8975a017917156b8824f936e.png:  invalid chunk name "m�&lt;%" (6d ffffffc0 3c 25)<br>
m4-a46ce91d8975a017917156b8824f936e.png  EOF while reading m�&lt;% data<br>
ERROR: m4-a46ce91d8975a017917156b8824f936e.png<br>
m5-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk IHDR (computed 74ad9407, expected 79bdf676)<br>
m5-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk cHRM (computed 925fc546, expected 925f0a46)<br>
m5-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 1-bit image<br>
m5-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk PLTE (computed a692a17f, expected 30a7a68a)<br>
m5-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
m5-a46ce91d8975a017917156b8824f936e.png  illegal (unless recently approved) unknown, public chunk IQND<br>
ERROR: m5-a46ce91d8975a017917156b8824f936e.png<br>
m6-a46ce91d8975a017917156b8824f936e.png  invalid tIME hour (57)<br>
m6-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk tIME (computed aabc53ed, expected 1182599c)<br>
m6-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk tEXt (computed 66adc021, expected 7185a4e1)<br>
m6-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk cHRM (computed d5736632, expected 925fc546)<br>
m6-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk PLTE (computed c436d4d4, expected 30a7a68a)<br>
m6-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk pHYs (computed df1d0254, expected 009a9c18)<br>
m6-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = 2 (unknown)<br>
ERROR: m6-a46ce91d8975a017917156b8824f936e.png<br>
m7-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk IHDR (computed bc4d1b77, expected 79bdf676)<br>
m7-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 4-bit image<br>
m7-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk PLTE (computed dce1e344, expected 30a7a68a)<br>
m7-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
m7-a46ce91d8975a017917156b8824f936e.png  EOF while reading IEND data<br>
ERROR: m7-a46ce91d8975a017917156b8824f936e.png<br>
m8-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk IHDR (computed 330deed7, expected 79bdf676)<br>
m8-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk tEXt (computed e6fcb7d3, expected 7185a4e1)<br>
m8-a46ce91d8975a017917156b8824f936e.png  invalid number of PLTE entries (256) for 2-bit image<br>
m8-a46ce91d8975a017917156b8824f936e.png  CRC error in chunk PLTE (computed 70cec9d7, expected 30a7a68a)<br>
m8-a46ce91d8975a017917156b8824f936e.png  zlib: inflate error = -3 (data error)<br>
ERROR: m8-a46ce91d8975a017917156b8824f936e.png<br>
Errors were detected in 15 of the 15 files tested.<br>
<br>
</code></pre>
<h3>c-m1-a4842373fc20cc42b8e023a329761915.png</h3>

<h3>c-m2-a4842373fc20cc42b8e023a329761915.png</h3>

<h3>m1-a4842373fc20cc42b8e023a329761915.png</h3>

<h3>m2-a4842373fc20cc42b8e023a329761915.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-a4842373fc20cc42b8e023a329761915.png  invalid sBIT length<br>
c-m1-a4842373fc20cc42b8e023a329761915.png  illegal (unless recently approved) unknown, public chunk aLTE<br>
c-m1-a4842373fc20cc42b8e023a329761915.png  hIST must follow PLTE<br>
c-m1-a4842373fc20cc42b8e023a329761915.png  illegal critical, safe-to-copy chunk IENc<br>
ERROR: c-m1-a4842373fc20cc42b8e023a329761915.png<br>
c-m2-a4842373fc20cc42b8e023a329761915.png  invalid sBIT length<br>
c-m2-a4842373fc20cc42b8e023a329761915.png  PLTE not allowed in grayscale image<br>
c-m2-a4842373fc20cc42b8e023a329761915.png:  invalid chunk name "" (00 60 00 20)<br>
c-m2-a4842373fc20cc42b8e023a329761915.png  EOF while reading  data<br>
ERROR: c-m2-a4842373fc20cc42b8e023a329761915.png<br>
m1-a4842373fc20cc42b8e023a329761915.png  CRC error in chunk IHDR (computed 93e1c829, expected 815467c7)<br>
m1-a4842373fc20cc42b8e023a329761915.png  invalid sBIT length<br>
m1-a4842373fc20cc42b8e023a329761915.png  illegal (unless recently approved) unknown, public chunk aLTE<br>
m1-a4842373fc20cc42b8e023a329761915.png  hIST must follow PLTE<br>
m1-a4842373fc20cc42b8e023a329761915.png  illegal critical, safe-to-copy chunk IENc<br>
ERROR: m1-a4842373fc20cc42b8e023a329761915.png<br>
m2-a4842373fc20cc42b8e023a329761915.png  CRC error in chunk IHDR (computed 93e1c829, expected 815467c7)<br>
m2-a4842373fc20cc42b8e023a329761915.png  invalid sBIT length<br>
m2-a4842373fc20cc42b8e023a329761915.png  PLTE not allowed in grayscale image<br>
m2-a4842373fc20cc42b8e023a329761915.png:  invalid chunk name "" (00 60 00 20)<br>
m2-a4842373fc20cc42b8e023a329761915.png  EOF while reading  data<br>
ERROR: m2-a4842373fc20cc42b8e023a329761915.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>ac6343a98f8edabfcc6e536dd75aacb0.png</h3>

<ul><li>Origin: <code>http://img516.imageshack.us/img516/5884/joker1xj9.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: ac6343a98f8edabfcc6e536dd75aacb0.png (75x74, 8-bit palette+trns, interlaced, -58.5%).<br>
<br>
</code></pre>
<h3>c-m1-aded9dc1dc9361363ad0b426c2ff1846.png</h3>

<h3>m1-aded9dc1dc9361363ad0b426c2ff1846.png</h3>

<ul><li>Origin: <code>http://www.hkb.bfh.ch/typo3temp/pics/9bcf3ae114.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  private (invalid?) IDAT row-filter type (224) (warning)<br>
c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid IDAT row-filter type (5)<br>
c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  private (invalid?) IDAT row-filter type (239) (warning)<br>
c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid IDAT row-filter type (31)<br>
c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid IDAT row-filter type (23)<br>
c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  zlib: inflate error = -3 (data error)<br>
c-m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid zTXt compression method (120)<br>
ERROR: c-m1-aded9dc1dc9361363ad0b426c2ff1846.png<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  CRC error in chunk IHDR (computed dd4d2ee5, expected ddfa2ee5)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  CRC error in chunk iCCP (computed ccfced7d, expected 256333a2)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  private (invalid?) IDAT row-filter type (224) (warning)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid IDAT row-filter type (5)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  private (invalid?) IDAT row-filter type (239) (warning)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid IDAT row-filter type (31)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid IDAT row-filter type (23)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  CRC error in chunk IDAT (computed 2a61b8b5, expected a796c5bb)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  zlib: inflate error = -3 (data error)<br>
m1-aded9dc1dc9361363ad0b426c2ff1846.png  invalid zTXt compression method (120)<br>
ERROR: m1-aded9dc1dc9361363ad0b426c2ff1846.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>affc57dfffa5ec448a0795738d456018.png</h3>

<ul><li>Origin: <code>http://images.mygirlyspace.com/myspacegraphics/images/graphics/prod_659_34483.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: affc57dfffa5ec448a0795738d456018.png (435x235, 8-bit palette+trns, non-interlaced, 91.5%).<br>
<br>
</code></pre>
<h3>b3ac9fdb7239f42c734921dfe790291b.png</h3>

<ul><li>Origin: <code>brokensuite:chrm_after_plte.png</code></li></ul>

<h4>Notes</h4>

<pre><code>b3ac9fdb7239f42c734921dfe790291b.png  cHRM must precede PLTE<br>
ERROR: b3ac9fdb7239f42c734921dfe790291b.png<br>
<br>
</code></pre>
<h3>b583e48e218193e4c287f033931a6314.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>b583e48e218193e4c287f033931a6314.png  invalid number of PLTE entries (0)<br>
ERROR: b583e48e218193e4c287f033931a6314.png<br>
<br>
</code></pre>
<h3>b59d7a023a8dcd112da2eb859004199a.png</h3>

<ul><li>Origin: <code>http://ruph.sopca.com/wp-content/uploads/arabic-ads-facebook1.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: b59d7a023a8dcd112da2eb859004199a.png (470x551, 32-bit RGB+alpha, non-interlaced, 96.8%).<br>
<br>
</code></pre>
<h3>c-m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png</h3>

<h3>m1-b68163a6a8e2ccf3c8ad2c70a26c1150.png</h3>

<h3>m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png</h3>

<h3>m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
c-m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png:  invalid chunk name "I�D" (49 1e ffffffba 44)<br>
c-m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png  EOF while reading I�D data<br>
ERROR: c-m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png<br>
m1-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m1-b68163a6a8e2ccf3c8ad2c70a26c1150.png:  invalid chunk name "@END" (40 45 4e 44)<br>
m1-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk @END<br>
ERROR: m1-b68163a6a8e2ccf3c8ad2c70a26c1150.png<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  first chunk must be IHDR<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk jHDR<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  first chunk must be IHDR<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk oFFU<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  first chunk must be IHDR<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk pHYY<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  first chunk must be IHDR<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  first chunk must be IHDR<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png:  invalid chunk name "IE�D" (49 45 ffffffba 44)<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  first chunk must be IHDR<br>
m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png  EOF while reading IE�D data<br>
ERROR: m2-b68163a6a8e2ccf3c8ad2c70a26c1150.png<br>
m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png  CRC error in chunk vpAg (computed f790b292, expected 09c59193)<br>
m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png  illegal (unless recently approved) unknown, public chunk aDAT<br>
m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png:  invalid chunk name "I�D" (49 1e ffffffba 44)<br>
m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png  EOF while reading I�D data<br>
ERROR: m3-b68163a6a8e2ccf3c8ad2c70a26c1150.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>c-m1-b977e74d9de1f6689fdd84c4e38830f5.png</h3>

<h3>c-m2-b977e74d9de1f6689fdd84c4e38830f5.png</h3>

<h3>m1-b977e74d9de1f6689fdd84c4e38830f5.png</h3>

<h3>m2-b977e74d9de1f6689fdd84c4e38830f5.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (249) (warning)<br>
c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  invalid IDAT row-filter type (13)<br>
c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (216) (warning)<br>
c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  invalid IDAT row-filter type (43)<br>
c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (236) (warning)<br>
c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (150) (warning)<br>
c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  invalid IDAT row-filter type (35)<br>
c-m1-b977e74d9de1f6689fdd84c4e38830f5.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-b977e74d9de1f6689fdd84c4e38830f5.png<br>
c-m2-b977e74d9de1f6689fdd84c4e38830f5.png  invalid zTXt compression method (13)<br>
c-m2-b977e74d9de1f6689fdd84c4e38830f5.png  zTXt keyword has control character(s) (26)<br>
c-m2-b977e74d9de1f6689fdd84c4e38830f5.png  zlib: inflate error = -3 (data error)<br>
c-m2-b977e74d9de1f6689fdd84c4e38830f5.png  invalid chunk length (too large)<br>
ERROR: c-m2-b977e74d9de1f6689fdd84c4e38830f5.png<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  CRC error in chunk IDAT (computed 1b3e1a53, expected 941ff572)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (249) (warning)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  invalid IDAT row-filter type (13)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (216) (warning)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  invalid IDAT row-filter type (43)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (236) (warning)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  private (invalid?) IDAT row-filter type (150) (warning)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  invalid IDAT row-filter type (35)<br>
m1-b977e74d9de1f6689fdd84c4e38830f5.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-b977e74d9de1f6689fdd84c4e38830f5.png<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  CRC error in chunk iCCP (computed 39b8032f, expected fcb2b1ed)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  CRC error in chunk pHYs (computed b81a8e3f, expected d2dd7efc)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  invalid zTXt compression method (13)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  CRC error in chunk zTXt (computed 9c724d55, expected 4c86832d)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  CRC error in chunk tEXt (computed d2166d05, expected ce38b7f9)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  zTXt keyword has control character(s) (26)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  CRC error in chunk zTXt (computed bf657e16, expected 8a471546)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  zlib: inflate error = -3 (data error)<br>
m2-b977e74d9de1f6689fdd84c4e38830f5.png  invalid chunk length (too large)<br>
ERROR: m2-b977e74d9de1f6689fdd84c4e38830f5.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>ba2b2b6e72ca0e4683bb640e2d5572f8.png</h3>

<ul><li>Origin: <code>http://www.dicts.info/img/ud/shirt.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: ba2b2b6e72ca0e4683bb640e2d5572f8.png (218x265, 32-bit RGB+alpha, non-interlaced, 83.2%).<br>
<br>
</code></pre>
<h3>bd927c8547634cdbdd22af0afe818a9b.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code><br>
</code></pre>
<h3>bf203e765c98b12f6c2b2c33577c730d.png</h3>

<ul><li>Origin: <code>brokensuite:offs_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>bf203e765c98b12f6c2b2c33577c730d.png  pCAL must precede IDAT<br>
bf203e765c98b12f6c2b2c33577c730d.png  sCAL must precede IDAT<br>
bf203e765c98b12f6c2b2c33577c730d.png  pHYs must precede IDAT<br>
bf203e765c98b12f6c2b2c33577c730d.png  oFFs must precede IDAT<br>
ERROR: bf203e765c98b12f6c2b2c33577c730d.png<br>
<br>
</code></pre>
<h3>c-m1-bfce28c0e44bc8d1824d48fbec5075e2.png</h3>

<h3>m1-bfce28c0e44bc8d1824d48fbec5075e2.png</h3>

<ul><li>Origin: <code>http://static.todoexpertos.com/fotos/48x48/mariplus23_Identicon.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-bfce28c0e44bc8d1824d48fbec5075e2.png  invalid cHRM white point 39594.5 0.329<br>
c-m1-bfce28c0e44bc8d1824d48fbec5075e2.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-bfce28c0e44bc8d1824d48fbec5075e2.png<br>
m1-bfce28c0e44bc8d1824d48fbec5075e2.png  CRC error in chunk gAMA (computed 22000143, expected 60fc6105)<br>
m1-bfce28c0e44bc8d1824d48fbec5075e2.png  invalid cHRM white point 39594.5 0.329<br>
m1-bfce28c0e44bc8d1824d48fbec5075e2.png  CRC error in chunk cHRM (computed ba8c0244, expected 9cba513c)<br>
m1-bfce28c0e44bc8d1824d48fbec5075e2.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-bfce28c0e44bc8d1824d48fbec5075e2.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>c0a76d267196727887d45de4889bec33.png</h3>

<ul><li>Origin: <code>brokensuite:length_offs.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c0a76d267196727887d45de4889bec33.png  invalid oFFs length<br>
ERROR: c0a76d267196727887d45de4889bec33.png<br>
<br>
</code></pre>
<h3>c1a4baf5d7c68d366d4d4f948f7295be.png</h3>

<ul><li>Origin: <code>brokensuite:gama_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c1a4baf5d7c68d366d4d4f948f7295be.png  gAMA must precede IDAT<br>
ERROR: c1a4baf5d7c68d366d4d4f948f7295be.png<br>
<br>
</code></pre>
<h3>c53911b0385c34a8204c30fdc14ea5cc.png</h3>

<h3>c-c53911b0385c34a8204c30fdc14ea5cc.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c53911b0385c34a8204c30fdc14ea5cc.png  CRC error in chunk IDAT (computed 35af061e, expected ae426082)<br>
c53911b0385c34a8204c30fdc14ea5cc.png  file doesn't end with an IEND chunk<br>
ERROR: c53911b0385c34a8204c30fdc14ea5cc.png<br>
c-c53911b0385c34a8204c30fdc14ea5cc.png  file doesn't end with an IEND chunk<br>
ERROR: c-c53911b0385c34a8204c30fdc14ea5cc.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>c-m1-c5a372c145ce25ce712959cd3b6df35e.png</h3>

<h3>m1-c5a372c145ce25ce712959cd3b6df35e.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid cHRM red point 168.412 42782.2<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (233) (warning)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (213) (warning)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (243) (warning)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid IDAT row-filter type (20)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (236) (warning)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid IDAT row-filter type (66)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid IDAT row-filter type (32)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  zlib: inflate error = -3 (data error)<br>
c-m1-c5a372c145ce25ce712959cd3b6df35e.png  illegal (unless recently approved) unknown, public chunk qTXt<br>
ERROR: c-m1-c5a372c145ce25ce712959cd3b6df35e.png<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid cHRM red point 168.412 42782.2<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  CRC error in chunk cHRM (computed c5335f2e, expected 9cba513c)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  CRC error in chunk IDAT (computed 81ad4d2f, expected b8ace67b)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (233) (warning)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (213) (warning)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (243) (warning)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid IDAT row-filter type (20)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  private (invalid?) IDAT row-filter type (236) (warning)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid IDAT row-filter type (66)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid IDAT row-filter type (32)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  CRC error in chunk IDAT (computed 5b00d204, expected f72e2fc4)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  invalid IDAT row-filter type (32)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  zlib: inflate error = -3 (data error)<br>
m1-c5a372c145ce25ce712959cd3b6df35e.png  illegal (unless recently approved) unknown, public chunk qTXt<br>
ERROR: m1-c5a372c145ce25ce712959cd3b6df35e.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>c5c030bf52b9b2d8c45c88988fafff4f.png</h3>

<ul><li>Origin: <code>brokensuite:bkgd_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c5c030bf52b9b2d8c45c88988fafff4f.png  bKGD must precede IDAT<br>
ERROR: c5c030bf52b9b2d8c45c88988fafff4f.png<br>
<br>
</code></pre>
<h3>c636287a4d7cb1a36362f7f236564cef.png</h3>

<ul><li>Origin: <code>brokensuite:splt_duplicate_name.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: c636287a4d7cb1a36362f7f236564cef.png (32x32, 8-bit palette, non-interlaced, -29.9%).<br>
<br>
</code></pre>
<h3>m1-cb265e4ae8967567fca5b0ecd58b90cb.png</h3>

<ul><li>Origin: <code>http://moj.name/files/logo.png</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-cb265e4ae8967567fca5b0ecd58b90cb.png  first chunk must be IHDR<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png  illegal (unless recently approved) unknown, public chunk pHDR<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png  first chunk must be IHDR<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png  illegal (unless recently approved) unknown, public chunk bKGj<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png  first chunk must be IHDR<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png  invalid tIME length<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png:  invalid chunk name "��;" (ffffffff 7f ffffffed 3b)<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png  first chunk must be IHDR<br>
m1-cb265e4ae8967567fca5b0ecd58b90cb.png  EOF while reading ��; data<br>
ERROR: m1-cb265e4ae8967567fca5b0ecd58b90cb.png<br>
<br>
</code></pre>
<h3>d2e515cfdabae699301dcf290382474d.png</h3>

<ul><li>Origin: <code>http://crohncolitis.foroactivo.com/users/40/21/63/avatars/30-41.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: d2e515cfdabae699301dcf290382474d.png (120x126, 32-bit RGB+alpha, non-interlaced, -81.2%).<br>
<br>
</code></pre>
<h3>c-d3ffec5786387c590721e674d705f16e.png</h3>

<h3>d3ffec5786387c590721e674d705f16e.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-d3ffec5786387c590721e674d705f16e.png  invalid IDAT row-filter type (112)<br>
c-d3ffec5786387c590721e674d705f16e.png  illegal (unless recently approved) unknown, public chunk aEND<br>
ERROR: c-d3ffec5786387c590721e674d705f16e.png<br>
d3ffec5786387c590721e674d705f16e.png  CRC error in chunk IHDR (computed 51ed9ceb, expected 6e096d3c)<br>
d3ffec5786387c590721e674d705f16e.png  invalid IDAT row-filter type (112)<br>
d3ffec5786387c590721e674d705f16e.png  illegal (unless recently approved) unknown, public chunk aEND<br>
ERROR: d3ffec5786387c590721e674d705f16e.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>d45b0dbbb808df6486f8a13ea44ea174.png</h3>

<ul><li>Origin: <code>brokensuite:offs_unit_specifier.png</code></li></ul>

<h4>Notes</h4>

<pre><code>d45b0dbbb808df6486f8a13ea44ea174.png  invalid oFFs unit specifier (2)<br>
ERROR: d45b0dbbb808df6486f8a13ea44ea174.png<br>
<br>
</code></pre>
<h3>m1-d4b25a2b8b5fcec0a3e284579d539f35.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-d4b25a2b8b5fcec0a3e284579d539f35.png  illegal (unless recently approved) unknown, public chunk fAMA<br>
m1-d4b25a2b8b5fcec0a3e284579d539f35.png  zlib: inflate error = -3 (data error)<br>
m1-d4b25a2b8b5fcec0a3e284579d539f35.png  cHRM must precede PLTE<br>
ERROR: m1-d4b25a2b8b5fcec0a3e284579d539f35.png<br>
<br>
</code></pre>
<h3>c-m1-d87a07bdc461bf81e43447ca0620d71d.png</h3>

<h3>m1-d87a07bdc461bf81e43447ca0620d71d.png</h3>

<h3>m2-d87a07bdc461bf81e43447ca0620d71d.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (238) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (5)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (252) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (60)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (108)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (186) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (208) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (8)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (137) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (117)<br>
c-m1-d87a07bdc461bf81e43447ca0620d71d.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-d87a07bdc461bf81e43447ca0620d71d.png<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  CRC error in chunk IDAT (computed 8ce08b76, expected d61f6723)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (238) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (250) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (251) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (5)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  CRC error in chunk IDAT (computed 53a6db55, expected f400847a)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (252) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (60)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (108)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (186) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (208) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (8)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  CRC error in chunk IDAT (computed 5089eb97, expected 3f12925d)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (137) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  private (invalid?) IDAT row-filter type (254) (warning)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  invalid IDAT row-filter type (117)<br>
m1-d87a07bdc461bf81e43447ca0620d71d.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-d87a07bdc461bf81e43447ca0620d71d.png<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png  first chunk must be IHDR<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png  illegal (unless recently approved) unknown, public chunk zHDR<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png  first chunk must be IHDR<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png  illegal reserved-bit-set chunk iCbP<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png  first chunk must be IHDR<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png:  invalid chunk name "vpA�" (76 70 41 ffffffdb)<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png  first chunk must be IHDR<br>
m2-d87a07bdc461bf81e43447ca0620d71d.png  invalid chunk length (too large)<br>
ERROR: m2-d87a07bdc461bf81e43447ca0620d71d.png<br>
Errors were detected in 3 of the 3 files tested.<br>
<br>
</code></pre>
<h3>d92428f3fc9c806b0a4373b54e06785e.png</h3>

<ul><li>Origin: <code>http://www.jmcraeproductions.com/Uploaded_Files/jmcraeproductions.com-Main1.png</code></li></ul>

<h4>Notes</h4>

<pre><code>d92428f3fc9c806b0a4373b54e06785e.png  invalid tIME length<br>
ERROR: d92428f3fc9c806b0a4373b54e06785e.png<br>
<br>
</code></pre>
<h3>dd18aac055d531e0e4ff8979458dbaa3.png</h3>

<ul><li>Origin: <code>brokensuite:splt_length_mod_6.png</code></li></ul>

<h4>Notes</h4>

<pre><code>dd18aac055d531e0e4ff8979458dbaa3.png  invalid number of sPLT entries (1.66667)<br>
ERROR: dd18aac055d531e0e4ff8979458dbaa3.png<br>
<br>
</code></pre>
<h3>c-m1-e0f25ec3373dfdca79ba7bcc3ad366f3.png</h3>

<h3>m1-e0f25ec3373dfdca79ba7bcc3ad366f3.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: c-m1-e0f25ec3373dfdca79ba7bcc3ad366f3.png (621x174, 32-bit RGB+alpha, non-interlaced, 52.5%).<br>
m1-e0f25ec3373dfdca79ba7bcc3ad366f3.png  CRC error in chunk zTXt (computed 8e5143e2, expected 9ced0937)<br>
ERROR: m1-e0f25ec3373dfdca79ba7bcc3ad366f3.png<br>
Errors were detected in 1 of the 2 files tested.<br>
No errors were detected in 1 of the 2 files tested.<br>
<br>
</code></pre>
<h3>m1-e275d32a37943b0d5eeb86ffb04b7cf2.png</h3>

<h3>m2-e275d32a37943b0d5eeb86ffb04b7cf2.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  illegal (unless recently approved) unknown, public chunk aHDR<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  illegal (unless recently approved) unknown, public chunk pHOs<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  illegal (unless recently approved) unknown, public chunk nDAT<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  tEXt keyword has control character(s) (143)<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m1-e275d32a37943b0d5eeb86ffb04b7cf2.png  no IDAT chunks<br>
ERROR: m1-e275d32a37943b0d5eeb86ffb04b7cf2.png<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  illegal (unless recently approved) unknown, public chunk aHDR<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  illegal (unless recently approved) unknown, public chunk oFFZ<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  illegal reserved-bit-set chunk lHns<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  zlib: inflate error = -3 (data error)<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  illegal (unless recently approved) unknown, public chunk tEXK<br>
m2-e275d32a37943b0d5eeb86ffb04b7cf2.png  first chunk must be IHDR<br>
ERROR: m2-e275d32a37943b0d5eeb86ffb04b7cf2.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>c-e585afb2ecf50c04eaf0dedb71602cb8.png</h3>

<h3>e585afb2ecf50c04eaf0dedb71602cb8.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-e585afb2ecf50c04eaf0dedb71602cb8.png  invalid bKGD length<br>
c-e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (24)<br>
c-e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (111)<br>
c-e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (115)<br>
c-e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (10)<br>
c-e585afb2ecf50c04eaf0dedb71602cb8.png  private (invalid?) IDAT row-filter type (131) (warning)<br>
c-e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (6)<br>
ERROR: c-e585afb2ecf50c04eaf0dedb71602cb8.png<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  CRC error in chunk IHDR (computed a9b9ca49, expected 3c0171e2)<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  invalid bKGD length<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (24)<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (111)<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (115)<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (10)<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  private (invalid?) IDAT row-filter type (131) (warning)<br>
e585afb2ecf50c04eaf0dedb71602cb8.png  invalid IDAT row-filter type (6)<br>
ERROR: e585afb2ecf50c04eaf0dedb71602cb8.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>e59ec0cfb8ab64558099543dc19f8378.png</h3>

<ul><li>Origin: <code>http://www.cg.opstinakotor.org/templates/opstina_kotor_2007/images/i_font_large_x.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: e59ec0cfb8ab64558099543dc19f8378.png (18x11, 1-bit palette+trns, interlaced, -672.7%).<br>
<br>
</code></pre>
<h3>e76546768d4a8f2f4c39339345c7614c.png</h3>

<ul><li>Origin: <code>brokensuite:length_phys.png</code></li></ul>

<h4>Notes</h4>

<pre><code>e76546768d4a8f2f4c39339345c7614c.png  invalid pHYs length<br>
ERROR: e76546768d4a8f2f4c39339345c7614c.png<br>
<br>
</code></pre>
<h3>c-ea01d6c175bb25dc75757cf8a5793822.png</h3>

<h3>ea01d6c175bb25dc75757cf8a5793822.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-ea01d6c175bb25dc75757cf8a5793822.png  private (invalid?) IHDR interlace method (130) (warning)<br>
c-ea01d6c175bb25dc75757cf8a5793822.png  EOF while reading tEXt data<br>
ERROR: c-ea01d6c175bb25dc75757cf8a5793822.png<br>
ea01d6c175bb25dc75757cf8a5793822.png  private (invalid?) IHDR interlace method (130) (warning)<br>
ea01d6c175bb25dc75757cf8a5793822.png  CRC error in chunk IHDR (computed 31086bbc, expected 498b65ef)<br>
ea01d6c175bb25dc75757cf8a5793822.png  CRC error in chunk gAMA (computed 37058ae9, expected 1f058ae9)<br>
ea01d6c175bb25dc75757cf8a5793822.png  EOF while reading tEXt data<br>
ERROR: ea01d6c175bb25dc75757cf8a5793822.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>ebfb1cd42314a557e72d4da75c21fc1c.png</h3>

<ul><li>Origin: <code>http://behance.vo.llnwd.net/profiles/83520/projects/135867/0835201223910993.png</code></li></ul>

<h4>Notes</h4>

<pre><code>OK: ebfb1cd42314a557e72d4da75c21fc1c.png (202x158, 32-bit RGB+alpha, non-interlaced, 84.2%).<br>
<br>
</code></pre>
<h3>ed5f2464fcaadd4e0a5e905e3ac41ad5.png</h3>

<ul><li>Origin: <code>brokensuite:scal_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>ed5f2464fcaadd4e0a5e905e3ac41ad5.png  pHYs must precede IDAT<br>
ed5f2464fcaadd4e0a5e905e3ac41ad5.png  sCAL must precede IDAT<br>
ERROR: ed5f2464fcaadd4e0a5e905e3ac41ad5.png<br>
<br>
</code></pre>
<h3>edf5c1b0aa5b01eea5017290a286a173.png</h3>

<ul><li>Origin: <code>http://tutihoko.web.infoseek.co.jp/bro7761.png</code></li></ul>

<h4>Notes</h4>

<pre><code>edf5c1b0aa5b01eea5017290a286a173.png  additional data after IEND chunk<br>
edf5c1b0aa5b01eea5017290a286a173.png  EOF while reading chunk length<br>
ERROR: edf5c1b0aa5b01eea5017290a286a173.png<br>
<br>
</code></pre>
<h3>c-f23a99688fa66359f6186678e6b2f14a.png</h3>

<h3>f23a99688fa66359f6186678e6b2f14a.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>c-f23a99688fa66359f6186678e6b2f14a.png  invalid IHDR sample depth (0)<br>
c-f23a99688fa66359f6186678e6b2f14a.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
ERROR: c-f23a99688fa66359f6186678e6b2f14a.png<br>
f23a99688fa66359f6186678e6b2f14a.png  invalid IHDR sample depth (0)<br>
f23a99688fa66359f6186678e6b2f14a.png  CRC error in chunk IHDR (computed 5ea996be, expected 6ed9dd7f)<br>
f23a99688fa66359f6186678e6b2f14a.png  private (invalid?) IDAT row-filter type (255) (warning)<br>
ERROR: f23a99688fa66359f6186678e6b2f14a.png<br>
Errors were detected in 2 of the 2 files tested.<br>
<br>
</code></pre>
<h3>f427b6bee1acd1fea3ec953bc556a18a.png</h3>

<ul><li>Origin: <code>brokensuite:plte_empty.png</code></li></ul>

<h4>Notes</h4>

<pre><code>f427b6bee1acd1fea3ec953bc556a18a.png  invalid number of PLTE entries (0)<br>
ERROR: f427b6bee1acd1fea3ec953bc556a18a.png<br>
<br>
</code></pre>
<h3>f5e7b9db8e8d002a26304f5c81889ee1.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>f5e7b9db8e8d002a26304f5c81889ee1.png  EOF while reading IHDR data<br>
ERROR: f5e7b9db8e8d002a26304f5c81889ee1.png<br>
<br>
</code></pre>
<h3>f6266c0e9c2f7db9fab0f84562f63b6c.png</h3>

<ul><li>Origin: <code>brokensuite:ster_after_idat.png</code></li></ul>

<h4>Notes</h4>

<pre><code>f6266c0e9c2f7db9fab0f84562f63b6c.png  sTER must precede IDAT<br>
ERROR: f6266c0e9c2f7db9fab0f84562f63b6c.png<br>
<br>
</code></pre>
<h3>f757de9794666c3d14985210679bc98c.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_phys.png</code></li></ul>

<h4>Notes</h4>

<pre><code>f757de9794666c3d14985210679bc98c.png  multiple pHYs not allowed<br>
ERROR: f757de9794666c3d14985210679bc98c.png<br>
<br>
</code></pre>
<h3>f85c09bb72db5a572d24b8d3a0d56542.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>f85c09bb72db5a572d24b8d3a0d56542.png  this is neither a PNG or JNG image nor a MNG stream<br>
ERROR: f85c09bb72db5a572d24b8d3a0d56542.png<br>
<br>
</code></pre>
<h3>fa9f6aa9bcc679d20e171dbf07a628fd.png</h3>

<ul><li>Origin: <code>brokensuite:multiple_gama.png</code></li></ul>

<h4>Notes</h4>

<pre><code>fa9f6aa9bcc679d20e171dbf07a628fd.png  multiple gAMA not allowed<br>
ERROR: fa9f6aa9bcc679d20e171dbf07a628fd.png<br>
<br>
<br>
<br>
</code></pre>
<h3>c-m1-fcac2d6a6a739e8ceb946ac99200d9f1.png</h3>

<h3>c-m2-fcac2d6a6a739e8ceb946ac99200d9f1.png</h3>

<h3>m1-fcac2d6a6a739e8ceb946ac99200d9f1.png</h3>

<h3>m2-fcac2d6a6a739e8ceb946ac99200d9f1.png</h3>

<ul><li>Origin: <code>http://www.schaik.com/pngsuite/ch1n3p04.png</code></li></ul>

<h4>Notes</h4>

<pre><code>c-m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  37 sBIT blue bits invalid for 8-bit/sample image<br>
c-m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  invalid number of PLTE entries (15) for 1-bit image<br>
c-m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  illegal (unless recently approved) unknown, public chunk pIST<br>
c-m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  zlib: inflate error = -3 (data error)<br>
ERROR: c-m1-fcac2d6a6a739e8ceb946ac99200d9f1.png<br>
c-m2-fcac2d6a6a739e8ceb946ac99200d9f1.png  zlib: inflate error = -3 (data error)<br>
c-m2-fcac2d6a6a739e8ceb946ac99200d9f1.png  EOF while reading fEND data<br>
ERROR: c-m2-fcac2d6a6a739e8ceb946ac99200d9f1.png<br>
m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  CRC error in chunk IHDR (computed 3eb3d821, expected 81546781)<br>
m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  CRC error in chunk gAMA (computed 31e8965f, expected 9fe8965f)<br>
m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  37 sBIT blue bits invalid for 8-bit/sample image<br>
m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  CRC error in chunk sBIT (computed 3b91a5fd, expected 77f8b5a3)<br>
m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  invalid number of PLTE entries (15) for 1-bit image<br>
m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  illegal (unless recently approved) unknown, public chunk pIST<br>
m1-fcac2d6a6a739e8ceb946ac99200d9f1.png  zlib: inflate error = -3 (data error)<br>
ERROR: m1-fcac2d6a6a739e8ceb946ac99200d9f1.png<br>
m2-fcac2d6a6a739e8ceb946ac99200d9f1.png  CRC error in chunk IHDR (computed f6535751, expected 9d5467c7)<br>
m2-fcac2d6a6a739e8ceb946ac99200d9f1.png  CRC error in chunk hIST (computed 44da2ff3, expected 48995941)<br>
m2-fcac2d6a6a739e8ceb946ac99200d9f1.png  zlib: inflate error = -3 (data error)<br>
m2-fcac2d6a6a739e8ceb946ac99200d9f1.png  EOF while reading fEND data<br>
ERROR: m2-fcac2d6a6a739e8ceb946ac99200d9f1.png<br>
Errors were detected in 4 of the 4 files tested.<br>
<br>
</code></pre>
<h3>fde6410fe7fb87f095bc855279d5beab.png</h3>

<ul><li>Origin: <code>Unknown</code></li></ul>

<h4>Notes</h4>

<pre><code>fde6410fe7fb87f095bc855279d5beab.png:  CORRUPTED by text conversion<br>
ERROR: fde6410fe7fb87f095bc855279d5beab.png<br>
<br>
</code></pre>
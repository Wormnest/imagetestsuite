# Introduction #

This document introduces how the testsuites are generated.


# Details #

The image testsuite uses a combination of techniques to generate a small number of samples with a high probability of achieving maximum code-coverage. This is done by finding a large number of publicly available images to generate a large test corpus, and then finding the smallest number of those images with the same code coverage as the larger set.

That is, if each unique line of code in an image decoder is considered a possible element, and each input image is considered a set of those elements, then this is an attempt to find the smallest union of those sets with same cardinality.

The code coverage is calculated using as many publicly available decoders as can be found. The resulting set of images are included here for testing.

Additionally, the original corpus is extended through random mutation (i.e. fuzzing) in order to try to explore as much error handling code as possible. The end result is a small set of images that, if handled by your decoder or application correctly, help improve test coverage and may expose implementation errors. Of course, 100% test coverage does not mean 100% bug free, but can help improve overall code quality.
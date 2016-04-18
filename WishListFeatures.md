# Wish list of things to improve/develop for the AIDA project #

## Introduction ##

There are a number of things we'd love to see improved for AIDA.  Below is a smattering.

## Details ##

  1. write how-to-use documentation and develop tutorials
  1. create a version in Python 3
  1. get FFTW working again
  1. create a GUI interface
  1. recaste the representation/optimization of the kernel/point spread function in a more compact, computationally efficient form
  1. create a robust approach to guess the system point spread function in cases where the user does not provide any guess
  1. improving the performance of image and point spread function pre-processing/cleaning modules
  1. translate some components (TBD) into faster C++ code
  1. develop a GPU (graphics processing unit) version of the code
  1. explore the use of AIDA to process images from consumer cameras
  1. improve automatic hyperparameter estimation scheme for point spread functions of large extent (currently violates approximation assumption and thus requires user-tweaking of the automatic estimates)
  1. develop the algorithm further to improve noise suppression, robust myopic decon, leverage inter-frame features in multi-frame image data
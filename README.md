# CNN visibility metric for selecting resolution of textures
> Please find more information here: http://texture-metrics.mpi-inf.mpg.de/

## Requirements

The metric was implemented using python (v 3.5.2) and Tensorflow (v 1.4.0) library.
Additionally, numpy and openCV libraries need to be installed.

## Preapring metric

To run the metric, please proceed with following steps:
1. Clone or download and unpack the repository.
2. Download the one of the network blobs from:

```
http://texture-metrics.mpi-inf.mpg.de/files/CNN-T-HDR-VDP-P94.zip
http://texture-metrics.mpi-inf.mpg.de/files/CNN-T-CNN-GP-P93.zip
http://texture-metrics.mpi-inf.mpg.de/files/CNN-T-Butteraugli-P93.zip
```

3. Unpack NetworkModel.zip file to repository root directory.
4. Done! 

## Interface

Only a python interface of our metric is provided. The interface takes reference and distorted images as inputs and returns a
visibility map. The visibility map values correspond to probability of detection by population, where higher value means the more likly detection.

The interface supports both, PNG and JPG, images as inputs. To get the visibility map, run:

```
python cnn_visibility.py -r referenceImage.{png|jpg} -t distortedImage.{png|jpg} -m modelPath
```

It is also possible to run metric using more files at the same time. If the corresponding reference and distorted images have the same names and are located in two sepatare directories run:

```
python cnn_visibility.py -r referenceDirectory/* -t distortedDirectory/* -m modelPath
```

The metric will autmatically pair images and process all of them. It is highly recommended to process more than one image same time, since libraries import and network loading processes take significant amount of time.

By default, the results will be saved in 'vismaps' directory, which is created automatically and located in metric root directory.
To direct the output to the custom directory use the third argument as shown below:

```
python cnn_visibility.py -r referenceDirectory/* -t distortedDirectory/* -m modelPath -d customDirectoryName 
```

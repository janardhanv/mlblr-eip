Deep Learning has revolutionised computer vision and it is the core technology behind capabilities like self-driving car. We use tensorflow and tensorflow implementation of Keras.

## Keras & TensorFlow:
TensorFlow is the most popular tool of deep learning and Keras is the popular API/interface for specifying DL models. Keras started as a standalone library for specifying deep learning models, which could then be run in TensorFlow as well as in other DL computation engines.

Standalone Keras library still exists but TensorFlow has become the dominant engine for DL, os the creator of Keras implemented a version of Keras, that's built into TensorFlow. This allows you to specify models with the elegant of Keras while taking greater advantage of some powerful TensorFlow features.

## How images are stored for ML?
Image is composed of pixels and pixels are present in rows and columns. So it is natural to store them in a matrix. For a black and white/grayscale image, each value represents darkness of pixel in a image. 

Colour images have an extra dimension. There are each matrices, with pixel in each matrix value showing how red/green/blue the pixel is. 

Tensor is the word for something like a matix but with which can have any number of dimensions. So these matrices could be called tensors.


## Convolution

Today's deep learning models apply something called convolutions to image tensors. A convolution is a small tensor that can be multiplied over little sections of a main image.

Depending on values in the convolution array, it can pick out specific patterns from the image.
eg: Horizontal line detector:

|1.5|1.5|
----|----
|-1.5|-1.5|

When multiplied on an image section with horizontal line, it results in a large value. When applied over a section without horizontal line, it gives a value close to zero.

Numerical value in the convolutin tensor decides what pattern it detects in a section of the image.

Once a filter is created, it is applied to each part of the image. Output is mapped to a output tensor. Thsi gives a map of where the associated pattern shows up in the image. 

Different convolutions/ filters captures different aspects of the original image. In practice, numbers in a filter/convolution are set by us during the training process using gradient descent & backpropogation processes.

Each convolution/filter applied to an 2D-image tensor results in a new 2D tensor. All the 2D tensors from different convolutions are stacked together to form a single 3D tensor.

For eg: there might be one tensor for vertical line detection, one for horizontal line detection. All these are stacked with tensors form other convolutions. Result is a reperesentaiton of the image in three dimensions. 

Moving across the first dimension means moving horizontaly through the image. Moving across second dimension means moving vertically through the image. Moving to the last dimension takes you from the output of one convolution to next. This last dimension is called channel dimension.

Next set of convolution is applied to the 3D tensor that we got as output from the first layer of convolutions. Each set of convolutions that get applied at a time is called a layer. So the first layer of convolution takes the raw pixel intensities and translated them into a 3D tensor, indicating horizontal lines, vertical lines, dark spots and so on. So the second layer of convolutions takes the map of pattern locations as input and multiplies them with 3D convolutions tof ind more interesting patterns.
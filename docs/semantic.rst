.. _semantic:

**SEMANTIC SEGMENTATION WITH PIXELLIB**
=========================================

PixelLib is implemented with Deeplabv3+ framework to perform semantic segmentation. Xception model trained on pascalvoc dataset is used for semantic segmentation.

*Code to implement semantic segmentation*:

.. code-block:: python

  import pixellib
  from pixellib.semantic import semantic_segmentation

  segment_image = semantic_segmentation()
  segment_image.load_pascalvoc_model("deeplabv3_xception_tf_dim_ordering_tf_kernels.h5") 
  segment_image.segmentAsPascalvoc("path_to_image", output_image_name = "path_to_output_image")



We shall take a look into each line of code.


.. code-block:: python

  import pixellib
  from pixellib.semantic import semantic_segmentation

  #created an instance of semantic segmentation class
  segment_image = semantic_segmentation()

The class for performing semantic segmentation is imported from pixellib and we created an instance of the class.

.. code-block:: python

  segment_image.load_pascalvoc_model("deeplabv3_xception_tf_dim_ordering_tf_kernels.h5") 

We called the function to load the xception model trained on pascal voc. The xception model can be download from `here <https://github.com/ayoolaolafenwa/PixelLib/releases/download/1.1/deeplabv3_xception_tf_dim_ordering_tf_kernels.h5>`_

.. code-block:: python

  segment_image.segmentAsPascalvoc("path_to_image", output_image_name = "path_to_output_image")

This is the line of code that performs segmentation on an image and the segmentation is done in the pascalvoc's color format. This function takes in two parameters:

  *path_to_image*: the path to the image to be segemented.

  *path_to_output_image*: the path to save the output image. The image will be saved in your current working directory.

**Sample1.jpg**  

.. image:: photos/sample1.jpg

Image's source: Pinterest

.. code-block:: python

  import pixellib
  from pixellib.semantic import semantic_segmentation

  segment_image = semantic_segmentation()
  segment_image.load_pascalvoc_model("deeplabv3_xception_tf_dim_ordering_tf_kernels.h5") 
  segment_image.segmentAsPascalvoc("sample1.jpg", output_image_name = "image_new.jpg")

.. image:: photos/result.jpg  


Your saved image with all the objects present segmented.

You can obtain an image with segmentation overlay on the objects with a modified code below.

.. code-block:: python

  segment_image.segmentAsPascalvoc("sample1.jpg", output_image_name = "image_new.jpg", overlay = True)

We added an extra parameter **overlay** and set it to **true**, we produced an image with segmentation overlay.

.. image:: photos/overlay.jpg



This xception model is trained on pascal voc dataset, a dataset with 20 object categories.

Objects and their corresponding colormaps.


.. image:: photos/pascal.png
.. _instance:

**INSTANCE SEGMENTATION WITH PIXELLIB**
=========================================


Instance segmentation with PixelLib is based on MaskRCNN framework.

*Code to implement instance segmentation*:

.. code-block:: python

  import pixellib
  from pixellib.instance import instance_segmentation

  segment_image = instance_segmentation()
  segment_image.load_model("mask_rcnn_coco.h5") 
  segment_image.segmentImage("path_to_image", output_image_name = "output_image_path")

*Observing each line of code:*

.. code-block:: python

  import pixellib
  from pixellib.instance import instance_segmentation

  segment_image = instance_segmentation()

The class for performing instance segmentation is imported and we created an instance of the class.

.. code-block:: python

  segment_image.load_model("mask_rcnn_coco.h5") 

This is the code to load the mask rcnn model to perform instance segmentation. Download the mask rcnn model from `here <https://github.com/ayoolaolafenwa/PixelLib/releases/download/1.2/mask_rcnn_coco.h5>`_

.. code-block:: python

  segment_image.segmentImage("path_to_image", output_image_name = "output_image_path")

This is the code to perform instance segmentation on an image and it takes two parameters:

  *path_to_image*: The path to the image to be predicted by the model.

  *output_image_name*: The path to save the segmentation result. It will be saved in your current working directory.

**Sample2.jpg**

.. image:: photos/sample2.jpg  

Image's source:Wikimedia




.. code-block:: python

  import pixellib
  from pixellib.instance import instance_segmentation

  segment_image = instance_segmentation()
  segment_image.load_model("mask_rcnn_coco.h5") 
  segment_image.segmentImage("sample2.jpg", output_image_name = "image_new.jpg")


.. image:: photos/masks.jpg  


This is the saved image in your current working directory. 

You can implement segmentation with bounding boxes. This can be achieved by modifying the code.

.. code-block:: python

  segment_image.segmentImage("sample2.jpg", output_image_name = "image_new.jpg", show_bboxes = True)

We added an extra parameter **show_bboxes** and set it to **true**, the segmentation masks are produced with bounding boxes.

.. image:: photos/maskboxes.jpg


You get a saved image with both segmentation masks and bounding boxes.

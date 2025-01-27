# Converting an ONNX Faster R-CNN Model {#openvino_docs_MO_DG_prepare_model_convert_model_onnx_specific_Convert_Faster_RCNN}

@sphinxdirective

The instructions below are applicable **only** to the Faster R-CNN model converted to the ONNX file format from the `maskrcnn-benchmark model <https://github.com/facebookresearch/maskrcnn-benchmark>`__:

1. Download the pretrained model file from `onnx/models <https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/faster-rcnn>`__ (commit-SHA: 8883e49e68de7b43e263d56b9ed156dfa1e03117).

2. Generate the Intermediate Representation of the model, by changing your current working directory to the model conversion API installation directory, and running model conversion with the following parameters:

   .. code-block:: sh

      mo \
      --input_model FasterRCNN-10.onnx \
      --input_shape [1,3,800,800] \
      --input 0:2 \
      --mean_values [102.9801,115.9465,122.7717] \
      --transformations_config front/onnx/faster_rcnn.json


   Be aware that the height and width specified with the ``input_shape`` command line parameter could be different. For more information about supported input image dimensions    and required pre- and post-processing steps, refer to the `Faster R-CNN article <https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/   faster-rcnn>`__.

3. Interpret the outputs of the generated IR: class indices, probabilities and box coordinates. Below are the outputs from the ``DetectionOutput`` layer:

   * class indices
   * probabilities
   * box coordinates

@endsphinxdirective

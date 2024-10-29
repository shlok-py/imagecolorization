## DeepLabv3 Generator Architecture

### 1. Encoder: ResNet-50

- **Input Modification**: Modified to accept 1-channel input.
- **Feature Extraction**: Utilizes layers up to the penultimate layer, producing feature maps of size [batch size, 2048, H/32, W/32].

### 2. Atrous Spatial Pyramid Pooling (ASPP)

- **1x1 Convolution**: Reduces input channels to a fixed number.
- **3x3 Convolutions with Different Dilation Rates**: Dilations of 3, 6, and 9 for multi-scale context.
- **Global Average Pooling**: Followed by 1x1 convolution and upsampling.
- **Concatenation**: Concatenates feature maps.
- **Final Convolution**: Reduces concatenated feature maps to desired output channels.

### 3. Decoder

- **Transposed Convolutional Layers**: Upsamples feature maps.
  - Each layer followed by batch normalization and ReLU activation.
- **Final Layer**: Transposed convolutional layer mapping output to 2 channels (ab channels).
https://huggingface.co/spaces/shlok123/imageColorization

goto above link for demo

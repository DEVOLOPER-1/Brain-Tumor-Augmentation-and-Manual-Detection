# Brain Tumor Detection and Augmentation Project

## Overview

This project involves processing a dataset of grayscale brain tumour images to create augmented data samples and generate masks for tumour detection. The tasks are performed using Google Colab and include various data augmentation techniques, mask creation, and image segmentation.

## Dataset
- Download the dataset and upload it to Google Colab.
- Unzip the archive file using the provided code.
- Read the dataset and preprocess the images:
  - Slice each image `[:, :, 0]` to ensure they are in grayscale.
  - Resize each image to `[256, 256]`.
  - Print the number of images in the dataset.

## Data Augmentation
Due to the small dataset size, augmentation techniques are used to create more samples:

### Crop
- Crop each image into four parts and resize each part to generate four new data samples.

### Flip
- Flip each image to generate a new data sample.
- Note: Do not use `numpy.flip` or any similar function.

### Rotate 90°
- Rotate each image by 90° to generate a new data sample.
- Note: Do not use `numpy.rot90` or any similar function.

## Mask Creation
- Use the `inRange` function to create masks from the dataset images.
- Determine the appropriate upper and lower range values to label the tumour using a colour picker.
- Multiply each image by its mask to segment the tumour and plot the result.

## Tumor Localization
- Iterate over each mask to find the indices needed to crop the tumour part:
  - Find four indices for each tumor `[row_start : row_end, column_start : column_end]`.
  - Note: Do not use `cv2.contour` or any similar function.

## X-Y Pair Creation
- Create two numpy arrays, `X` and `Y`:
  - `X` contains the dataset images.
  - `Y` contains the masks created for tumours.
  - `X` shape: `(num_of_images, height, width)`
  - `Y` shape: `(num_of_images, height, width)`

## Requirements
- Python 3.x
- Google Colab
- NumPy
- OpenCV
- Matplotlib

## Usage
1. Clone the repository and upload the dataset to Google Colab.
2. Follow the code cells in the provided Colab notebook to preprocess the dataset, perform data augmentation, create masks, and generate X-Y pairs.
3. Execute each section of the notebook sequentially to replicate the results.

## Results
The processed images and masks can be visualized within the Colab notebook. The results include augmented images, segmented tumors, and localized tumour regions.

## Contributing
Contributions are welcome! Please create a pull request with a detailed description of your changes.

## License
This project is licensed under the Unlicense.

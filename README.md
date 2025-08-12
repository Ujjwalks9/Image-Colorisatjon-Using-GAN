# Image Colorization with PyTorch

This project demonstrates how to build and train a Convolutional Neural Network (CNN) in PyTorch to perform automatic image colorization. The goal is to take a grayscale input image and generate a plausible RGB output. By training on the CIFAR-10 dataset, the model learns the mapping between grayscale and color versions of images.

This type of system can be applied in multiple domains such as restoring historical black-and-white photographs, colorizing artistic sketches, or enhancing images in media production workflows.

## Features

* End-to-end CNN-based model (`ColorizationNet`) for grayscale-to-color mapping
* Training pipeline using CIFAR-10
* RGB to HSV conversion utilities for improved color manipulation
* Adjustable saturation and brightness to enhance outputs
* Side-by-side visualization utilities for analysis
* Support for processing custom input images after training

## Image Output
<img width="1790" height="428" alt="image_output" src="https://github.com/user-attachments/assets/504556a8-82a4-4fb8-987a-64d5218e2d47" />


## How It Works

The model architecture is composed of four convolutional layers with dilated kernels to capture wider contextual information from the input image. The first three layers use ReLU activation for non-linearity, and the final layer uses Sigmoid activation to produce normalized RGB outputs.

The training process includes converting CIFAR-10 images to grayscale for input while using the original colored images as targets. The loss function is Mean Squared Error (MSE), optimized with Adam.

A post-processing step can be applied to enhance saturation and brightness in HSV color space.

## Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/image-colorization.git
cd image-colorization
```

2. (Optional) Set up a virtual environment:

```bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```

3. Install required dependencies:

```bash
pip install torch torchvision matplotlib pillow
```

## Usage

### Training on CIFAR-10

```bash
python colorize_model2.py
```

This will:

* Download and prepare CIFAR-10
* Train the model for 30 epochs
* Display training loss at regular intervals
* Show results on test images using the built-in visualization function

### Colorizing a Custom Image

Edit the code to load your image:

```python
img = Image.open('your_image.jpg')
```

Run:

```bash
python colorize_model2.py
```

The model will:

* Convert your image to grayscale
* Generate a colorized version
* Save it as `_colorized2.jpg`
* Display original, grayscale, and generated images side-by-side

## Model Architecture

| Layer | Input Channels | Output Channels | Kernel | Padding | Dilation |
| ----- | -------------- | --------------- | ------ | ------- | -------- |
| Conv1 | 1              | 64              | 5x5    | 4       | 2        |
| Conv2 | 64             | 64              | 5x5    | 4       | 2        |
| Conv3 | 64             | 128             | 5x5    | 4       | 2        |
| Conv4 | 128            | 3               | 5x5    | 4       | 2        |

## Color Enhancement

Function `exaggerate_colors()`:

* Boosts saturation (`saturation_factor`, default: 1.5)
* Boosts brightness (`value_factor`, default: 1.2)
* Operates in HSV color space before converting back to RGB

## Requirements

* Python 3.8+
* PyTorch
* Torchvision
* Matplotlib
* Pillow

## License

MIT License — you are free to use, modify, and distribute this project.

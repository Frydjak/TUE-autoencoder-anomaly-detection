# anomaly-Detection-with-autoencoder
This project is part of the (cannot explicitly name it due to plagiarism prevention) course at TU Eindhoven. It aims to implement anomaly detection in MNIST dataset using autoencoder structure. Anomaly in form of added noise is getting detected by increased loss in reconstructed images. This metric is being used to detect anomalies. Additionally, different network structures have been compared for this case.

## Dataset
The project is based on the [MNIST dataset](https://en.wikipedia.org/wiki/MNIST_database), which consists of 28x28 grayscale images of handwritten digits. The dataset is widely used for training and testing in the field of machine learning. To simulate anomalies a Gaussian noise of different strength has been added to samples in corrupted set.

image 1

## Implementation
### FCN Simple Autoencoder

### FCN Improved Autoencoder

### CNN Autoencoder

## Running the code

### Environment Setup
It is recommended to use the course-provided "experiments_JF" environment to run the code.

### Dataset Download
The Datasets folder contains a zipped file of the MNIST dataset. This dataset includes all samples without any division into training, testing, or validation sets. To run the code, please unzip the file manually.

## Remarks
- Model saving and loading has been implemented.
- Technically, project has not been fully completed due to time constrains, but meaningful results have been achieved.
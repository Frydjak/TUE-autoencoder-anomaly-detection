# Autoencoder Anomaly Detection
This project is part of the (cannot explicitly name it due to plagiarism prevention) course at TU Eindhoven. It aims to implement anomaly detection in MNIST dataset using autoencoder structure. Anomaly in form of added noise is getting detected by increased loss in reconstructed images. This metric is being used to detect anomalies. Additionally, different network structures have been compared for this case.

<img src="https://github.com/user-attachments/assets/924845cf-3eb8-48a9-b3ed-7b463f7356fe" width="100%">
resulting loss for normal sample: 0.006<br><br>



<img src="https://github.com/user-attachments/assets/96beb588-5948-46d4-a1d2-0dc2088f3962" width="100%">
resulting loss for corrupted sample: 0.021

## Dataset
The project is based on the [MNIST dataset](https://en.wikipedia.org/wiki/MNIST_database), which consists of 28x28 grayscale images of handwritten digits. The dataset is widely used for training and testing in the field of machine learning. To simulate anomalies a Gaussian noise of different strength has been added to samples in corrupted set.

<img src="https://github.com/user-attachments/assets/725031f7-26a5-42f8-897b-815891e0773d" width="500">

## Implementation
### FCN Simple Autoencoder
Model consists of two symmetrical components, made out of fully connected neural networks and uses ReLU activations

**Model Structure:** <br>
Encoder 784 -> 128 -> 64 -> 16  
Decoder 16 -> 64 -> 128 -> 784<br><br>
The final layer uses a Sigmoid activation to constrain the output values to the range [0,1].

Reconstruction:<br>
<img src="https://github.com/user-attachments/assets/d61bebf1-62eb-40c1-9096-78f2dcafeacf" width="500">
<img src="https://github.com/user-attachments/assets/f6182d51-c8cf-4bcb-89f9-8003c57049e3" width="500">

Proposed simple model was insufficient for appropriate performance. Reconstructed image seemed to
be an averaged number based on all samples. No significant loss increase was observed when reconstructing
from noisy images compared to originals, therefore it wasn't a suitable solution for anomaly detection.

### FCN Improved Autoencoder
Again, model consists of two symmetrical components, made out of fully connected neural networks and uses ReLU activations. This time more layers with larger hidden dimensions have been used.

**Model Structure:** <br>
Encoder 784 -> 512 -> 256 -> 128 -> 16  
Decoder 16 -> 128 -> 256 -> 512 -> 784<br><br>
The final layer uses a Sigmoid activation to constrain the output values to the range [0,1].

**Reconstruction:** <br>
<img src="https://github.com/user-attachments/assets/2c6e58a1-0407-4712-893f-bbfa4042e49c" width="500">
<img src="https://github.com/user-attachments/assets/500c5de8-f738-4add-ad96-40f6dd9e2f2d" width="500">

Results were greatly improved with reconstructed images resembling originals, however loss difference between original and noisy samples was insigificant.

### CNN Autoencoder
The CNN-based autoencoder uses convolutional layers for encoding and transposed convolutions for decoding. This structure captures spatial features more effectively than a fully connected architecture.

**Model Structure:** <br>
Encoder 28x28x1 -> 14x14x16 -> 7x7x32  
Decoder 7x7x32 -> 14x14x16 -> 28x28x1<br><br>

**Reconstruction:**<br>
<img src="https://github.com/user-attachments/assets/037acfe3-c4ad-4036-b355-01644669fd7c" width="500">
<img src="https://github.com/user-attachments/assets/20e1192e-62ae-4e2f-97d2-b49de551bb17" width="500">

Although the model is significantly simpler than Autoencoder_FCN_improved, it achieves better image reconstruction quality. As a result, it more clearly distinguishes between normal and noisy images, reflected in a higher reconstruction loss for anomalies.

## Results
Clearly corrupted samples can be distinguished from unchanged ones by tresholding with satisfactory results.  
<img src="https://github.com/user-attachments/assets/8a35d8f9-adf5-4bf1-b6f4-1f6c0166a23e" width="1000">
<img src="https://github.com/user-attachments/assets/26d03514-539f-4f90-be1a-3ba1dcc8ee51" width="500">

## Running the code
### Environment Setup
It is recommended to use the course-provided "experiments_JF" environment to run the code.

### Dataset Download
The Datasets folder contains a zipped file of the MNIST dataset. This dataset includes all samples without any division into training, testing, or validation sets. To run the code, please unzip the file manually.

## Remarks
- Model saving and loading has been implemented.
- Technically, project has not been fully completed due to time constrains, but meaningful results have been achieved.

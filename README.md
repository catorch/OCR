# OCR Model for Character Recognition (Chars74K-Digital-English-Font)

## Project Overview
This project focuses on creating a robust Optical Character Recognition (OCR) model using the Chars74K-Digital-English-Font dataset. The OCR model is built on top of the MobileNetV2 architecture and is capable of recognizing 62 different characters, including digits (0-9), uppercase letters (A-Z), and lowercase letters (a-z).

The project involves several stages, including data preparation, model training, character segmentation, and prediction. The model is trained using TensorFlow and Keras libraries, and the character segmentation is performed using OpenCV.

## Project Structure

### Data Preparation
The dataset is organized into separate folders for each character and is split into training and validation sets. The data is then loaded and preprocessed using the `ImageDataGenerator` class from Keras, ensuring proper normalization and resizing of the images.

### Model Training
The model is built using the following steps:
- Load the MobileNetV2 architecture as the base model.
- Freeze the base layers to utilize the pre-trained weights.
- Add custom layers, including a GlobalAveragePooling2D layer, a Dense layer, and a Dropout layer, to adapt the model to our specific task.
- Compile the model using the Adam optimizer and categorical_crossentropy loss function.
- Train the model using the preprocessed data from the `ImageDataGenerator`.

### Character Segmentation
Character segmentation is performed using OpenCV by:
- Converting the Region of Interest (ROI) to grayscale.
- Applying binary thresholding to segment the characters.
- Finding contours and drawing bounding boxes around each character.

### Character Prediction
After segmenting the characters, the model predicts the class of each character by:
- Preprocessing each character image to match the input requirements of the model.
- Predicting the class using the trained model.
- Mapping the predicted class index to the corresponding character using an `index_to_char` dictionary.

### Visualization
The characters, along with their bounding boxes, are visualized using `cv2_imshow`.

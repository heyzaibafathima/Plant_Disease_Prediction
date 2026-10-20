# Plant Disease Prediction System

## Project Overview

The Plant Disease Prediction System is a machine learning project that identifies plant diseases from leaf images using a **Convolutional Neural Network (CNN)**.

The model is trained using labelled plant leaf images and learns to recognize patterns associated with different plant diseases. The trained model is saved in `.keras` format and deployed using Streamlit to provide a simple and interactive web application where users can upload a leaf image and view the predicted disease.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Model Training](#model-training)
- [Saving the Trained Model](#saving-the-trained-model)
- [Setting Up the Streamlit Application](#setting-up-the-streamlit-application)
- [Running the Application](#running-the-application)
- [Usage](#usage)
- [Project Workflow](#project-workflow)
- [Future Enhancements](#future-enhancements)

## Features

- Predicts plant diseases from leaf images using a CNN.
- Supports image uploads in JPG, JPEG, and PNG formats.
- Resizes and preprocesses images before prediction.
- Uses a trained CNN model to classify plant leaf images.
- Maps predicted class indices to disease names using a JSON file.
- Saves the trained model for reuse without retraining.
- Provides an interactive web interface using Streamlit.

## Technologies Used

- **Python** – Programming language
- **Jupyter Notebook / Google Colab** – Model training and experimentation
- **TensorFlow and Keras** – Building, training, and loading the CNN model
- **NumPy** – Image array processing and numerical operations
- **Pillow (PIL)** – Opening and resizing images
- **JSON** – Storing and loading class index mappings
- **Streamlit** – Building the web application
- **PyCharm** – Developing and running the application
- **PlantVillage Dataset** – Plant leaf images for training and evaluation

## Project Structure

```text
PlantDiseasePrediction/
│
├── model_training_notebook/
│   └── Plant_Disease_Prediction.ipynb
│
├── app/
│   ├── app.py
│   ├── plant_disease_prediction_model.keras
│   └── class_indices.json
│
└── README.md
```

*Note: Adjust the notebook folder and filename to match your actual project structure.*

### File Description

- **Plant_Disease_Prediction.ipynb** – Contains the code for loading the dataset, preprocessing images, building the CNN, training the model, and evaluating its performance.
- **plant_disease_prediction_model.keras** – Stores the trained CNN model used to predict plant diseases.
- **class_indices.json** – Stores the mapping between numerical class indices and plant disease names.
- **app.py** – Contains the Streamlit application code for uploading images, preprocessing them, and displaying predictions.
- **README.md** – Provides project details, setup instructions, and usage information.

## Getting Started

### Prerequisites

Install the following before running the project:

- Python
- PyCharm or another Python IDE
- Required Python libraries
- The trained CNN model and class mapping JSON file

Install the required libraries using:

```bash
pip install tensorflow numpy pillow streamlit
```

## Model Training

The CNN model is trained using a Jupyter Notebook or Google Colab.

1. Download and load the labelled plant leaf image dataset.
2. Organize the images into their corresponding disease classes.
3. Preprocess the images and prepare them for training.
4. Split the data into training and validation sets.
5. Build the CNN architecture using convolutional, pooling, and dense layers.
6. Compile the model using an optimizer, loss function, and evaluation metrics.
7. Train the model using the `fit()` method.
8. Evaluate its performance using validation results.
9. Save the trained model for use in the Streamlit application.

The CNN uses the following layers:

- **Conv2D** – Extracts useful visual features from leaf images.
- **ReLU** – Introduces non-linearity into the network.
- **MaxPooling2D** – Reduces feature map dimensions.
- **Flatten** – Converts feature maps into a one-dimensional vector.
- **Dense** – Learns relationships between extracted features.
- **Softmax output layer** – Produces class probabilities for multi-class classification.

## Saving the Trained Model

After training, save the model using Keras:

```python
model.save("plant_disease_prediction_model.keras")
```

Here, `model` represents the trained CNN.

The `.keras` file stores the trained model so that the Streamlit application can load it without repeating the training process.

The class index mapping should also be saved as `class_indices.json` so the predicted numerical index can be converted into the corresponding disease name.

## Setting Up the Streamlit Application

1. Open PyCharm and create or open the `PlantDiseasePrediction` project.
2. Create an `app` folder if it does not already exist.
3. Place the trained `.keras` model inside the `app` folder.
4. Place `class_indices.json` in the same folder.
5. Create a Python file named `app.py`.
6. Import the required libraries, including TensorFlow, NumPy, Pillow, JSON, and Streamlit.
7. Load the trained model using `tf.keras.models.load_model()`.
8. Create an image preprocessing function to resize images to 224 × 224, convert them into NumPy arrays, add a batch dimension, and normalize pixel values.
9. Create a prediction function that obtains the predicted class index and maps it to a disease name.
10. Build the interface using Streamlit image upload, preview, and classification controls.

Make sure the model path in `app.py` points to the actual location of the `.keras` file.

## Running the Application

Open the terminal in PyCharm, navigate to the application folder, and execute:

```bash
python -m streamlit run app.py
```

Streamlit will display a local URL in the terminal, usually:

```text
http://localhost:8501
```

Open this URL in your browser to access the Plant Disease Prediction System.

## Usage

1. Open the Streamlit application in your browser.
2. Upload a plant leaf image in JPG, JPEG, or PNG format.
3. Preview the uploaded image.
4. Click the **Classify** button.
5. The application preprocesses the image and passes it to the trained CNN.
6. The model predicts the class with the highest score.
7. The application displays the predicted plant disease name.

The application uses the saved model to perform predictions without retraining the CNN whenever the application starts.

## Project Workflow

The project follows these steps:

**PlantVillage Dataset → Image Preprocessing → CNN Architecture → Model Training → Model Evaluation → Save `.keras` Model → Streamlit Application → Upload Leaf Image → Disease Prediction**

## Future Enhancements

- Improve generalization using data augmentation and regularization techniques.
- Add confidence scores to the prediction results.
- Add an unknown-image detection mechanism for unsupported images.
- Improve model performance using additional diverse plant leaf images.
- Provide basic information about predicted diseases and possible prevention methods.
- Deploy the application online for wider accessibility.

## Conclusion

The Plant Disease Prediction System demonstrates how deep learning can be used for image classification. By combining a Convolutional Neural Network with Streamlit, the project provides a simple interface for uploading plant leaf images and obtaining disease predictions.

This project provides practical experience in image preprocessing, CNN architecture, model training, model evaluation, model saving, and deploying a machine learning model through an interactive application.

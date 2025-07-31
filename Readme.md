# **Emotion Based Music Recommender**

This project is an Emotion Based Music Recommender that captures your facial and hand gestures through your webcam, predicts your current emotion using a trained deep learning model, and recommends songs on YouTube based on detected emotion, preferred language, and singer.

## **Table of Contents**

* [Overview](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#overview)  
* [Features](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#features)  
* [Project Structure](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#project-structure)  
* [Setup & Installation](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#setup--installation)  
* [Data Collection](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#data-collection)  
* [Model Training](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#model-training)  
* [Running the Application](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#running-the-application)  
* [Troubleshooting](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#troubleshooting)  
* [Dependencies](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#dependencies)  
* [Notes](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#notes)  
* [License](https://www.perplexity.ai/search/import-streamlit-as-st-from-st-RM0IFgqQSQu70Iip6Jv1Bg#license)

## **Overview**

The system uses MediaPipe Holistic to track facial, left hand, and right hand landmarks in live video feed. These landmarks are preprocessed and input to a Keras deep learning model trained to classify emotions.  
Based on the predicted emotion, your input language, and the singer name, the app recommends YouTube song results matching the emotion and preferences.

## **Features**

* Real-time face and hand landmark tracking via webcam  
* Deep learning model for emotion classification  
* User input for preferred song language and singer  
* YouTube song recommendations based on emotional state  
* Streamlit UI for an interactive and easy-to-use interface

## 

## **Project Structure**

text

`.`  
`├── Data_Collection.py   # Script to capture video landmarks and save as .npy data`  
`├── Data_Training.py     # Script to load .npy files, train model, and save model.h5 & labels.npy`  
`├── Test.py              # Streamlit app running emotion detection and recommending songs`  
`├── model.h5             # Trained Keras model (generated after training)`  
`├── labels.npy           # Label array associated with classes (generated after training)`  
`├── emotion.npy          # Temporary file to store detected emotion (runtime)`  
`└── README.md            # This documentation file`

## **Setup & Installation**

1. Clone the repository:  
2. bash

`git clone https://github.com/your-username/emotion-music-recommender.git`  
`cd emotion-music-recommender`

3.   
4. Create and activate a virtual environment (recommended):  
5. bash

`python3 -m venv venv`  
`source venv/bin/activate  # On Windows: venv\Scripts\activate`

6.   
7. Install required packages:  
8. bash

`pip install -r requirements.txt`

9.   
10. If you don’t have requirements.txt, install manually:  
11. bash

`pip install streamlit streamlit-webrtc mediapipe opencv-python-headless numpy tensorflow keras`

12.   
13. Verify your environment:  
14. Confirm required hardware drivers for GPU (optional) and Python version compatibility.

## 

## **Data Collection**

Use Data\_Collection.py to capture landmark data samples for different emotions:

* Make sure your webcam is connected.  
* Run the script:  
* bash

`python Data_Collection.py`

*   
* Enter the name of the emotion label (e.g., happy, sad) when prompted.  
* The script will capture 100 frames of facial and hand landmarks.  
* A .npy file with the label name will be saved.

Repeat the process for all emotions you want to classify.

## **Model Training**

The Data\_Training.py script loads all .npy files (except labels.npy), concatenates data and labels, builds a neural network model, trains it, and saves the model and labels:

* Run:  
* bash

`python Data_Training.py`

*   
* The model will train for 50 epochs by default.  
* After training, it creates model.h5 and labels.npy for use in the app.

Note: Ensure sufficient system memory is available and that .npy files are not corrupted.

## **Running the Application**

Start the Streamlit web app to detect emotion and recommend songs:  
bash

`streamlit run Test.py`

* Input your preferred language and singer.  
* Allow webcam access; your face and hand landmarks will be tracked in real-time.  
* Your detected emotion will be displayed on the video.  
* Click Recommend me songs to open a YouTube search with parameters including your emotion, language, and singer.

## **2\. Indentation or Syntax Errors**

Make sure your Python files follow correct indentation rules, especially inside loops and class methods.

## **Dependencies**

| Package | Version (tested) |
| :---- | :---- |
| Python | 3.8+ |
| streamlit | latest |
| streamlit\_webrtc | latest |
| mediapipe | latest stable |
| opencv-python-headless | latest |
| tensorflow | 2.x |
| keras | 2.x |
| numpy | latest |

## **Notes**

* The app uses real-time webcam video stream; high CPU/GPU load expected.  
* Data collection requires clean, consistent landmark captures per emotion.  
* Larger models or datasets require more RAM during training.  
* Make sure your environment supports WebRTC video streaming used in Streamlit.  
* The music recommendation opens YouTube in your default browser.


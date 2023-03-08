---
name: RespAI
tools: [CNN, COVID-19, featured]
image: ../assets/img/respAI1.png
description: A web app to detect COVID-19 and Pneumonia from Chest X-Ray images using a Deep Convolutional Neural Network.
---

```md
> ⚠ Disclaimer: This application is meant for educational purposes only and should not be used in a real-world context.
```

## Contents:

1. [Background](#background)
2. [Problem definition](#problem)
   1. [CT scan radiation](#ctscan)
   2. [Cost and time effective](#cost)
   3. [Accessibility](#accessibility)
3. [Functionalities](#functionalities)
   1. [Web application](#webapp)
   2. [CNN](#cnn)
   3. [Prediction of COVID-19 results](#results)
   4. [Probability](#probability)
   5. [Patient database](#db)
4. [Architecture](#architecture)
5. [Links](#links)
6. [Team](#team)

<div class="m-3" id="background">
    <br />
    <h2>📚 Background:</h2>
</div>

The coronavirus pandemic has invoked panic within every individual in the world. With rising cases everyday, it is essential to find a quick way to detect the virus, thus giving more time for treatment. Analyzing Chest X-rays has proved to be an effective method for testing Pneumonia and COVID 19, given that CT scans are expensive. However, it can be time consuming and difficult to analyze lots of CXR images. To deal with this issue, in this study, we have leveraged Convolutional Neural Networks (CNNs) to automate the diagnosis of Pneumonia and COVID 19 from the CXR image produced by the user, which can be a patient or doctor. RespAI takes a CXR image as input and classifies it into three classes: Covid 19, pneumonia and normal, within a short period of time. To implement RespAI, we use a Deep CNN. The data used to train the model consists of CXR of patients with covid 19 and pneumonia and those of normal people. This data is augmented to increase training efficiency and prevent the model from overfitting. The model is trained and tested, taking into consideration the fact that false negatives are intolerable. Along with this, a database of every patient will also be maintained containing their past health records which can be accessed by doctors.

<div class="m-3" id="problem">
    <br />
    <h2>🎯 Problem definition:</h2>
</div>

<div class="m-3" id="ctscan">
    <br />
    <h4>1. CT scan radiation:</h4>
</div>

CT scans are an effective method used to detect COVID, but it increases the risk of exposing patients to high levels of radiation. This method has been under scrutiny since it exposes patients to a very high level of radiation known to increase the probability of cancer. As quoted by the AIIMS Director, one CT Scan is equivalent to around 300-400 Chest X-rays.

Hence, in this report, we will be using a deep learning approach to predict COVID 19 results from Chest X-ray images avoiding the effects of radiation. RespAI takes a CXR image as input and classifies it into three classes: Covid 19, pneumonia and normal, within a short period of time.

<div class="m-3" id="cost">
    <br />
    <h4>2. Cost and Time effective:</h4>
</div>

Along with the risk of radiation, CT scans are also expensive and might not be affordable for certain patients. In a few cases, the results take a few hours or days to be produced. Due to this limitation, it is not available for everyone to use it. Getting a quick result might be difficult and costly.
In this model, instead of CT scans we will be using Chest X-Ray images which are more cost effective, thus making it more usable. Once a Chest X-ray is obtained, it is a simple procedure to obtain the result using RespAI within a few minutes.

<div class="m-3" id="accessibility">
    <br />
    <h4>3. Accessibility:</h4>
</div>

COVID 19 tests are usually built in a way so as to be used in clinical settings at home and need elaborate arrangements and equipment. Some countries lack these requirements and this delays the production of results, affecting many patients’ health.
RespAI is a web app which is platform independent and accessible as it can be used anywhere, anytime. The application is linked with the patient’s history so as to aid the doctors in analysing his/her condition. Because of its flexibility, anyone can use it by simply uploading CXR images and getting the required results.

<div class="m-3" id="functionalities">
    <br />
    <h2>✅ Functionalities:</h2>
</div>

<div class="m-3" id="webapp">
    <br />
    <h4>1. Web application:</h4>
</div>

RespAI will be a web application with very convenient and accessible features. One main functionality is being able to upload CXR images for results. Using html, css javascript for frontend and python for backend, this functionality has been made such that uploading X ray images and displaying the results is done in a short period of time.

<div class="m-3" id="cnn">
    <br />
    <h4>2. CNN (Convolutional Neural Network):</h4>
</div>

This project involves creation of a Deep learning based Convolutional Neural Network (CNN) using Keras (python library) and integrating the model with a front-end user interface for ease of use. This leads up to the creation of a software which we have named as RespAI. It uses the sequential Keras model which is built layer by layer, which then gives the final output. The proposed approach gives a classification accuracy of 99%.

<div class="m-3" id="results">
    <br />
    <h4>3. Prediction of COVID-19 results:</h4>
</div>

After implementing the CNN approach on the CXR images provided, all the layers are trained independently to make independent predictions which are then combined to give the final output. The model is built such that the positive or negative covid results are displayed on the screen in a few minutes.

<div class="m-3" id="probability">
    <br />
    <h4>4. Probability:</h4>
</div>

It includes the probability of the result. Depending on the images, this model also gives a probability result to determine the surety of it. This information helps the radiologist/doctor to make a clinical decision.

<div class="m-3" id="db">
    <br />
    <h4>5. Patient database:</h4>
</div>

This application also includes a complete database of the patient which contains the patient's details history. This aids the doctors in inspecting the patient’s condition depending on their history, thus taking necessary precautions.

<div class="m-3" id="architecture">
    <br />
    <h2>🏙 Architecture:</h2>
</div>

<div class="mermaid" align='center'>
flowchart LR
subgraph models
B[VGG16 \n weights = imagenet]
C[DenseNet201 \n weights = imagenet]
end
subgraph layer1
D[Concatenate] --> E[AvgPooling2D] --> F[Flatten]
end
subgraph layer2
G[Dense 128] --> H[Relu]
end
subgraph layer3
I[Dense 64] --> J[Relu] --> K[Dropout 0.5]
end
subgraph layer4
L[Dense 3] --> M[Softmax]
end
A[Chest X-Ray] --> B & C --> layer1 --> layer2 --> layer3 --> layer4 --> Output
</div>

<div class="m-3" id="links">
    <br />
    <h2>🚀 Links:</h2>
</div>

- [Prototype](https://respai.herokuapp.com/)
- [Application repo](https://github.com/Nilavan/RespAI)
- [Model code](https://www.kaggle.com/nilavanakilan/respai-cnn-training)
- [Model download](https://github.com/Nilavan/RespAI/releases/tag/model)
- [Dataset](https://www.kaggle.com/nilavanakilan/covid19pneumonia-cxrs)

<div class="m-3" id="team">
    <br />
    <h2>🌏 Team:</h2>
</div>

- Vaishalee R
- A Nilavan
- Pallavi Manasa <a class='fab fa-linkedin' data-toggle='tooltip' data-placement='bottom' data-delay='250' href='https://www.linkedin.com/in/pallavi-mokkarala-054883204'>

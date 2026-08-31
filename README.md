# Handwritten Mathematical Equation Solver

A full-stack application that recognizes and solves handwritten mathematical expressions and equations from an image or digital sketchpad.

The system uses Optical Character Recognition (OCR), Convolutional Neural Networks (CNN), image processing, and symbolic computation to convert handwritten mathematical content into machine-readable equations and generate the corresponding solution.

## Features

- Recognizes handwritten mathematical characters
- Supports drawing equations using a digital sketchpad
- Supports uploading handwritten equation images
- Performs image preprocessing and character segmentation
- Uses a CNN-based model for character recognition
- Supports arithmetic expressions such as addition, subtraction, multiplication, and division
- Solves mathematical equations of different degrees
- Provides a REST API for communication between the frontend and backend
- Supports Docker-based execution

## Tech Stack

### Frontend
- React.js
- JavaScript
- React-P5
- React Bootstrap

### Backend
- Python
- FastAPI
- REST API

### Machine Learning & Computer Vision
- TensorFlow / Keras
- Convolutional Neural Networks (CNN)
- OpenCV
- Optical Character Recognition (OCR)
- EMNIST dataset
- Image preprocessing
- Character segmentation

### Mathematical Processing
- SymPy
- Mathematical expression parsing and evaluation

### Deployment
- Docker
- Docker Compose

## System Architecture

```text
                 Handwritten Equation
                         │
                ┌────────┴────────┐
                │                 │
          Image Upload       Digital Sketchpad
                │                 │
                └────────┬────────┘
                         │
                         ▼
                 React.js Frontend
                         │
                    REST API
                         │
                         ▼
                  FastAPI Backend
                         │
                         ▼
                Image Preprocessing
                         │
                         ▼
              Character Segmentation
                         │
                         ▼
                CNN Character Model
                         │
                         ▼
             Equation Reconstruction
                         │
                  ┌──────┴──────┐
                  │             │
              Expression     Equation
                  │             │
                  ▼             ▼
              Evaluation     SymPy Solver
                  │             │
                  └──────┬──────┘
                         ▼
                     Solution


## Project Structure

```text
handwritten-mathematical-equation-solver/
├── api/
│   ├── app.py
│   ├── calculator.py
│   ├── main.py
│   ├── mapper.csv
│   ├── model.h5
│   ├── segmentor.py
│   ├── requirements.txt
│   └── templates/
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── Dockerfile
├── images/
├── docker-compose.yaml
└── README.md

## Key Features

- Handwritten mathematical equation recognition
- Image upload and digital sketchpad input
- Character segmentation using OpenCV
- Character recognition using a CNN trained on EMNIST
- Support for arithmetic expressions and mathematical equations
- Equation solving using SymPy
- REST API built with FastAPI
- React.js-based frontend
- Docker Compose support for local deployment

## How It Works

1. The user uploads an image or draws a handwritten equation using the sketchpad.
2. The React.js frontend converts the image into Base64 format and sends it to the FastAPI backend.
3. OpenCV preprocesses the image through binarization, thresholding, noise removal, and character segmentation.
4. The segmented characters are passed to the CNN model trained on the EMNIST dataset for character recognition.
5. The recognized characters are reconstructed into a mathematical expression or equation.
6. Arithmetic expressions are evaluated, while mathematical equations are solved using SymPy.
7. The final solution is returned to the frontend and displayed to the user.


## Installation

### Prerequisites

- Python 3.9+
- Node.js and npm
- Docker

### Backend Setup

```bash
cd api
pip install -r requirements.txt
uvicorn app:app --port 8000 --reload

### Frontend Setup

Open a new terminal:

```bash
cd frontend
npm install
npm run start
docker-compose up --build


## Equation Processing

The system processes handwritten equations through the following stages:

### 1. Image Preprocessing

OpenCV is used to preprocess the input image through noise removal, binarization, thresholding, and character segmentation.

### 2. Character Recognition

The segmented characters are passed to a CNN model trained on the EMNIST dataset. The model predicts the individual characters present in the handwritten equation.

### 3. Equation Reconstruction

The predicted characters are combined to reconstruct the mathematical expression or equation.

### 4. Expression Evaluation

For arithmetic expressions such as `5+3` or `66*3+2`, the reconstructed expression is evaluated to obtain the result.

### 5. Equation Solving

For equations containing `=`, the reconstructed expression is processed and solved using the SymPy symbolic mathematics library. The system supports linear and higher-degree polynomial equations.

## Character Segmentation

Character segmentation is an important preprocessing step in the recognition pipeline.

The image processing pipeline includes:

- Noise removal
- Image binarization
- Thresholding
- Line detection
- Character segmentation

The segmented characters are then passed individually to the CNN character recognition model.

## Equation Solver

After character recognition, the predicted characters are reconstructed into a mathematical expression.

The system handles two types of input:

### Arithmetic Expressions

Expressions such as:

```text
5+3
66*3+2
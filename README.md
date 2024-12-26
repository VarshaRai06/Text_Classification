# Text Classification API using SVM

This repository provides a **FastAPI-based API** for text classification, powered by a pre-trained **Support Vector Machine (SVM)** model.

---

## Key Features

- **Text Classification**: Classify input text into pre-defined categories.
- **Prediction Confidence**: Return the probability associated with the predicted category.
- **Performance Tracking**: Logs and tracks the time taken to perform each prediction.

---

## Project Directory Layout

```plaintext
├── app
│   ├── routes.py
│   └── main.py
├── model
│   ├── train.py
│   ├── predict.py
│   ├── svm_model.pkl
│   └── monitor.py
├── venv
├── .gitignore
├── dataset.xlsx
├── requirements.txt
```

---

## Description of Files and Folders

- **`app/main.py`**: The entry point for the FastAPI application.
- **`app/routes.py`**: Defines the API endpoints and handles incoming requests.
- **`model/predict.py`**: Houses the `ModelPredictor` class, responsible for loading the trained model and making predictions.
- **`model/train.py`**: Contains logic for training the SVM model and saving it as a file.
- **`model/monitor.py`**: A module with a decorator that tracks and logs prediction times.
- **`requirements.txt`**: A file that lists all the required dependencies for the project.
- **`.gitignore`**: Specifies which files and directories to exclude from version control.
- **`svm_model.pkl`**: The SVM model file, generated after training (not included; use `train.py` to create it).
- **`dataset.xlsx`**: The dataset file (Excel format) containing the "text" and "label" columns, used for training.
- **`venv`**: The virtual environment folder that contains the Python packages.
- **`README.md`**: Documentation outlining the project, including setup instructions and usage.

---

## Setup Instructions

Follow these steps to get the project up and running:

### Clone the Repository:
```bash
git clone https://github.com/your-username/svm-text-classification-api.git
```

### Navigate to the Project Folder:
```bash
cd svm-text-classification-api
```

### Set up a Virtual Environment (Optional but Recommended):
```bash
python -m venv venv
```

### Activate the Virtual Environment:

- **For Windows:**
  ```bash
  venv\Scripts\activate
  ```
- **For macOS/Linux:**
  ```bash
  source venv/bin/activate
  ```

### Install the Required Dependencies:
```bash
pip install -r requirements.txt
```

---

## Model Training

### To Train the SVM Model:

1. **Prepare Your Dataset**:
   Ensure your dataset is in Excel (`.xlsx`) format, with `text` and `label` columns.

2. **Modify `train.py`**:
   Update the `data_path` variable in `train.py` to point to your dataset.

3. **Run the Training Script**:
   ```bash
   python model/train.py
   ```
   This will train the model and save it as `svm_model.pkl`.

---

## Running the API Server

To start the API server, run:

```bash
uvicorn app.main:app --reload
```

The server will be live, and you can now send requests to it.

---

## Making Predictions

To make a prediction, send a **POST** request to the `/predict/` endpoint with the following JSON payload:

```json
{
  "text": "I love this movie"
}
```

### Response:

```json
{
  "status": "success",
  "data": {
    "prediction": "positive",
    "probability": [0.2, 0.8]
  }
}
```

---

## Contributions

We welcome contributions! Feel free to create issues or submit pull requests to improve the project.

---

## License

This project is licensed under the **MIT License**.

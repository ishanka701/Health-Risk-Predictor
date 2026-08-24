# Health Risk Predictor

A Streamlit web app that predicts a person's health risk level based on lifestyle and health-related inputs, using a pre-trained machine learning model.

## Features

- Interactive UI built with Streamlit
- Predicts risk level (e.g., Low / Medium / High) based on user inputs
- Visualizes lifestyle factors (Diet, Exercise, Sleep, Stress, BMI) in a bar chart using Plotly

## Inputs

| Feature | Type | Range / Options |
|---|---|---|
| Age | Slider | 18 - 80 |
| Diet Quality | Dropdown | Poor, Average, Good |
| Exercise Days per Week | Slider | 0 - 7 |
| Sleep Hours | Slider | 3 - 12 |
| Stress Level | Dropdown | Low, Medium, High |
| BMI | Number input | 10.0 - 40.0 |
| Smoking | Dropdown | Yes, No |
| Alcohol Consumption | Dropdown | Low, Medium, High |
| Family History of Disease | Dropdown | Yes, No |

## How It Works

1. The user enters their lifestyle and health details through the sidebar/main inputs.
2. Categorical inputs are encoded using pre-fitted `LabelEncoder` objects (`label_encoders.pkl`).
3. The encoded feature vector is passed to a pre-trained model (`Health_risk_predict.pkl`) to generate a prediction.
4. The predicted risk level is decoded back to its original label and displayed.
5. A bar chart of the entered lifestyle factors is rendered using Plotly.

## Project Structure

```
.
├── app.py                     # Main Streamlit application
├── Health_risk_predict.pkl    # Trained ML model
├── label_encoders.pkl         # Dictionary of LabelEncoders for categorical features
├── requirements.txt           # Python dependencies
└── README.md
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/health-risk-predictor.git
   cd health-risk-predictor
   ```

2. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the app locally with:

```bash
streamlit run app.py
```

Then open the local URL shown in the terminal (usually `http://localhost:8501`) in your browser.

## Requirements

```
streamlit
numpy
plotly
scikit-learn
```

> Note: `scikit-learn` is required even though it isn't imported directly in `app.py`, since the pickled model and encoders depend on it for unpickling.

## Model Files

This app expects two pickle files in the project root:

- `Health_risk_predict.pkl` — the trained classification model
- `label_encoders.pkl` — a dictionary of `LabelEncoder` objects keyed by feature name (`diet`, `stress`, `smoking`, `alcohol`, `family_history`, `risk_level`)

Make sure these files are generated from the same training pipeline/version of scikit-learn to avoid unpickling errors.

## Disclaimer

This tool is for educational/demonstration purposes only and is **not** a substitute for professional medical advice, diagnosis, or treatment.

## License

[MIT](LICENSE)

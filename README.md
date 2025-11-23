# Education in Africa - School Life Expectancy Prediction

## Mission and Problem

This project addresses the critical challenge of understanding how government education expenditure impacts school life expectancy across African countries. By analyzing the relationship between education investment (primary, secondary, and tertiary levels) and educational outcomes, we develop a predictive model to estimate expected years of schooling. The model enables policymakers and stakeholders to forecast educational outcomes based on budget allocation patterns, supporting data-driven decisions for improving education systems in Africa.

## API Endpoint

The prediction API is publicly available and can be accessed via Swagger UI for interactive testing:

**API Base URL:** `https://education-model-api.onrender.com`

**Swagger UI Documentation:** `https://education-model-api.onrender.com/docs`

**Prediction Endpoint:** `POST https://education-model-api.onrender.com/predict`

**Flutter App Repositry:** `https://github.com/NzizaPacifique250/edication_predictor_app.git`

The API accepts JSON input with the following parameters:
- `year` (integer, 2000-2030): Year of data
- `exp_primary_gdp` (float, 0-10%): Government expenditure on primary education as % of GDP
- `exp_secondary_gdp` (float, 0-10%): Government expenditure on secondary education as % of GDP
- `exp_tertiary_gdp` (float, 0-10%): Government expenditure on tertiary education as % of GDP
- `total_exp_gdp` (float, 0-25%): Total government expenditure on education as % of GDP

**Example Request:**
```json
{
  "year": 2020,
  "exp_primary_gdp": 2.5,
  "exp_secondary_gdp": 1.8,
  "exp_tertiary_gdp": 0.7,
  "total_exp_gdp": 5.0
}
```

**Example Response:**
```json
{
  "predicted_school_life_expectancy": 12.45,
  "input_data": {
    "year": 2020,
    "exp_primary_gdp": 2.5,
    "exp_secondary_gdp": 1.8,
    "exp_tertiary_gdp": 0.7,
    "total_exp_gdp": 5.0
  },
  "model_info": {
    "model_type": "Random Forest",
    "features": ["year", "exp_primary_gdp", "exp_secondary_gdp", "exp_tertiary_gdp", "total_exp_gdp"],
    "unit": "years"
  }
}
```

**Additional Endpoints:**
- `GET /health` - Health check endpoint to verify API and model status
- `GET /input-ranges` - Get valid input parameter ranges and descriptions
- `GET /docs` - Interactive Swagger UI documentation
- `GET /redoc` - Alternative API documentation

## Setup and Installation

### Prerequisites

- Python 3.8 or higher
- pip (Python package installer)

### Local Setup Instructions

1. **Navigate to the API directory:**
   ```bash
   cd summative/API
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment:**
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

4. **Install required dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
   
   The `requirements.txt` file includes the following packages:
   - `fastapi==0.104.1` - Web framework for building the API
   - `uvicorn==0.24.0` - ASGI server to run the API
   - `pydantic==2.5.0` - Data validation using Python type annotations
   - `joblib==1.3.2` - For loading the trained model
   - `numpy>=1.26.0` - Numerical computing library
   - `scikit-learn>=1.3.2` - Machine learning library
   - `python-multipart==0.0.6` - For handling multipart form data

5. **Ensure model files are present:**
   Make sure the following files are in the `API` directory:
   - `best_model.pkl` - Trained machine learning model
   - `scaler.pkl` - Feature scaler used during training
   - `feature_names.pkl` - Feature names (if needed)
   - `prediction.py` - Main API application file

6. **Run the API server:**
   ```bash
   uvicorn prediction:app --reload
   ```
   
   Or using Python directly:
   ```bash
   python prediction.py
   ```

7. **Access the API:**
   - API will be available at: `http://localhost:8000`
   - Interactive documentation (Swagger UI): `http://localhost:8000/docs`
   - Alternative documentation (ReDoc): `http://localhost:8000/redoc`
   - Health check: `http://localhost:8000/health`

### Testing the API

You can test the API using the Swagger UI at `http://localhost:8000/docs` or by making a POST request:

**Using curl:**
```bash
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{
    "year": 2020,
    "exp_primary_gdp": 2.5,
    "exp_secondary_gdp": 1.8,
    "exp_tertiary_gdp": 0.7,
    "total_exp_gdp": 5.0
  }'
```

**Using Python:**
```python
import requests

url = "http://localhost:8000/predict"
data = {
    "year": 2020,
    "exp_primary_gdp": 2.5,
    "exp_secondary_gdp": 1.8,
    "exp_tertiary_gdp": 0.7,
    "total_exp_gdp": 5.0
}

response = requests.post(url, json=data)
print(response.json())
```

## Video Demo

**YouTube Video Demo:** https://youtu.be/a2i492JF32o

The video demonstration (maximum 5 minutes) showcases the model's functionality, API usage, and prediction capabilities.


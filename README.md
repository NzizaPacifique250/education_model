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

## Video Demo

**YouTube Video Demo:** https://youtu.be/a2i492JF32o

The video demonstration (maximum 5 minutes) showcases the model's functionality, API usage, and prediction capabilities.


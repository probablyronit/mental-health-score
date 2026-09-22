# Mental Health Signal — Student Wellness Analytics

This project is a machine learning-powered web application that predicts a student's **Mental Health Score** based on their digital habits, demographics, and lifestyle metrics. The application uses a trained Machine Learning model to evaluate inputs such as screen time, sleep hours, study patterns, and platform usage to provide a score from 0 to 10.

It is designed as an informational tool to help students reflect on their daily habits and understand how their lifestyle may impact their mental well-being.

## Features
- **Predictive Analytics**: Calculates a mental health score out of 10 based on user input.
- **Interactive UI**: A modern, responsive frontend that visually displays the resulting score using an animated gauge.
- **Robust API**: A FastAPI backend that handles validation and interfaces with the pre-trained ML model.
- **Real-time Validation**: Client-side and server-side validation to ensure input constraints are met.

## Tech Stack
- **Frontend**: HTML5, CSS3, JavaScript
- **Backend**: FastAPI, Pydantic, Uvicorn
- **Machine Learning**: Python, Scikit-learn, Pandas, Joblib
- **Data Preprocessing**: Handled natively within the pipeline serialized in `Mental_Health_Model.pkl`.

## Project Structure
- `main.py` - The FastAPI backend application and API routes.
- `index.html` - The frontend web interface.
- `script.js` - Client-side logic, API integration, and UI interactions (like the gauge).
- `style.css` - Styling for the web application.
- `Mental_Health_Model.pkl` - The trained machine learning model exported via Joblib.
- `ML_Project.ipynb` - Jupyter Notebook containing the exploratory data analysis, data preprocessing, and model training.
- `Student Social Media And Mental Health Impact.csv` - The original dataset used to train the model.
- `requirements.txt` - Python dependencies required to run the backend.

## Dataset
The model was trained on the `Student Social Media And Mental Health Impact.csv` dataset, which contains 5000+ records of students detailing their:
- **Demographics**: Age, Gender, Country, Academic Level
- **Digital Habits**: Most used platform, Purpose of use, Avg daily usage hours, Daily unlocks
- **Lifestyle**: Study hours, Physical activity hours, Sleep hours, Perceived stress level

## Installation and Setup

1. **Clone the repository** (or download the source code):
   ```bash
   git clone <repository-url>
   cd Mental-Health-Score-main
   ```

2. **Set up a Python virtual environment** (Recommended):
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install backend dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the FastAPI server**:
   ```bash
   uvicorn main:app --port 8000 --reload
   ```
   *Note: In `script.js`, you may need to update the `API_BASE` variable to point to `http://localhost:8000` for local development if it's currently pointing to a deployed URL.*

5. **Open the application**:
   Simply open `index.html` in your web browser. 

## API Endpoints
### `POST /predict`
Evaluates the student data and returns the predicted mental health score.

**Request Body (JSON)**:
```json
{
  "age": 21,
  "gender": "Male",
  "country": "India",
  "academic_level": "Undergraduate",
  "most_used_platform": "Instagram",
  "purpose_of_use": "Entertainment",
  "avg_daily_usage_hours": 4.5,
  "daily_unlocks": 85,
  "study_hours": 3.0,
  "physical_activity_hours": 1.5,
  "sleep_hours_per_night": 7.5,
  "stress_level": "Medium"
}
```

**Response**:
```json
{
  "predicted_mental_health_score": 7.5
}
```

## Disclaimer
*This tool is built for informational purposes only. It is not a clinical assessment. If you are struggling with your mental health, please reach out to a professional or someone you trust.*

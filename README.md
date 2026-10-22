
# Patient Management System API

A RESTful API built using **FastAPI and Python** to manage patient records, validate patient information, calculate Body Mass Index (BMI), and generate BMI-based health categories.

This project demonstrates REST API development, data validation with Pydantic, CRUD operations, HTTP error handling, and automatic API documentation.

## ✨ Features

- **Create Patient Records:** Add new patients with validated information.
- **View Patient Records:** Retrieve all patient records or fetch an individual patient by ID.
- **Update Patient Records:** Modify existing patient information.
- **Delete Patient Records:** Remove patient records using their IDs.
- **Automatic BMI Calculation:** Calculate BMI using patient height and weight.
- **Health Assessment:** Classify BMI into Underweight, Normal, Overweight, or Obese categories.
- **Patient Sorting:** Sort records by height, weight, or BMI in ascending or descending order.
- **Data Validation:** Validate patient fields and enforce constraints using Pydantic.
- **Error Handling:** Return appropriate HTTP errors for missing patients, duplicate IDs, and invalid parameters.
- **Interactive API Documentation:** Explore and test endpoints using Swagger UI.

## 🛠️ Tech Stack

- **Language:** Python
- **Backend Framework:** FastAPI
- **Data Validation:** Pydantic
- **Data Storage:** JSON file
- **ASGI Server:** Uvicorn (if used to run the application)

## 🧠 How It Works

1. A client sends an HTTP request to the FastAPI application.
2. Incoming patient data is validated using Pydantic models.
3. Patient records are read from or written to a JSON file.
4. BMI is calculated automatically using height and weight.
5. A health category is generated from the calculated BMI.
6. The API returns a JSON response with the requested data or an appropriate error message.

### BMI Calculation

BMI is calculated using the formula:

`BMI = Weight (kg) / Height (m)²`

| BMI Range | Category |
|---|---|
| Below 18.5 | Underweight |
| 18.5 to below 25 | Normal |
| 25 to below 30 | Overweight |
| 30 and above | Obese |

*BMI categories are general screening classifications, not a medical diagnosis.*

## 📂 Project Structure

```text
fastapi-patient-management/
├── README.md
├── main.py
└── patients.json
```

- `main.py` — FastAPI application, patient models, validation, BMI calculation, and API endpoints.
- `patients.json` — JSON file used to store patient records.
- `README.md` — Project documentation.

## 🌐 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Welcome message |
| GET | `/about` | API description |
| GET | `/view` | Retrieve all patient records |
| GET | `/patient/{patient_id}` | Retrieve a patient by ID |
| GET | `/sort?sort_by=bmi&order=asc` | Sort patients by height, weight, or BMI |
| POST | `/create` | Create a new patient |
| PUT | `/edit/{patient_id}` | Update an existing patient |
| DELETE | `/delete/{patient_id}` | Delete a patient by ID |

## 📖 API Documentation

FastAPI automatically generates interactive documentation when the application is running.

- **Swagger UI:** `/docs`
- **ReDoc:** `/redoc`

Use these interfaces to inspect endpoints, submit requests, and view API responses.

## 🧪 Example Patient Request

Send a `POST` request to `/create` with the following JSON body:

```json
{
  "id": "P006",
  "name": "Aarav Sharma",
  "city": "Chandigarh",
  "age": 25,
  "gender": "male",
  "height": 1.75,
  "weight": 70
}
```

The API validates the supplied fields and calculates the patient's BMI and health category.

The `id` must be unique. Height and weight must be positive, age must be between 1 and 119, and gender must match an allowed value.

## ⚠️ Limitations

- Patient records are stored in a local JSON file rather than a database.
- JSON file storage is suitable for learning and small demonstrations but is not ideal for concurrent writes or production workloads.
- The application does not currently implement authentication or role-based access control.
- BMI-based categories are informational and should not be interpreted as a clinical diagnosis.

## 🔮 Future Improvements

- Integrate a relational database such as PostgreSQL.
- Add authentication and authorization.
- Introduce automated unit and integration tests.
- Add pagination and advanced patient search.
- Improve configuration and error handling.
- Containerize the application using Docker.

## 👨‍💻 Author

**Parv Sharma**

GitHub: [@Parv21Sharma](https://github.com/Parv21Sharma)

---

Built as a learning project to practice backend development and REST API design with FastAPI.

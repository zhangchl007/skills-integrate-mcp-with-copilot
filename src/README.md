# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teacher login for admin actions
- Sign up for activities (teachers only)
- Unregister students from activities (teachers only)

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/auth/login`                                                     | Teacher login (returns auth token)                                 |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up for an activity (requires teacher token)                   |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student (requires teacher token)                  |

## Teacher credentials

Teacher usernames and passwords are stored in `teachers.json` and checked by the backend.

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.

# Employee Attendance System with Face Recognition

This project is a Streamlit-based web application for employee attendance management using facial recognition and geolocation. It allows employees to check in and out by taking a photo and verifying their location. Admins can manage employee records, download attendance logs, and remove employees securely.

## Features
- **Face Recognition**: Uses a custom-trained MTCNN and ResNet model for employee identification.
- **Geolocation Verification**: Ensures attendance is only marked within a specified distance from the company location.
- **Admin Dashboard**:
  - Add new employees by uploading or capturing face images.
  - Remove employees from the system.
  - Download attendance records as CSV.
- **Attendance Page**:
  - Employees take a photo to check in/out.
  - Only recognized employees can submit attendance.
  - Location is automatically detected and verified.

## Setup Instructions
1. **Clone the repository and navigate to the project folder.**
2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Place your trained model files** (`mtcnn.pth` and `resnet.pth`) in the project directory.
4. **Set admin credentials** (see below).
5. **Run the app:**
   ```bash
   streamlit run app.py
   ```

## File Structure
- `app.py` — Main Streamlit application.
- `requirements.txt` — Python dependencies.
- `mtcnn.pth`, `resnet.pth` — Trained face recognition models (`resnet.pth` is not included; train it with `facial model.ipynb`).
- `admin_credentials.example.json` — Template for local admin credentials.
- `employees.csv`, `attendance.csv` — Created automatically at runtime. They hold face embeddings and location logs, so they are git-ignored and never committed.

## Admin Credentials
The app reads credentials in this order:

1. Streamlit secrets — `.streamlit/secrets.toml` (or the Streamlit Cloud secrets panel):
   ```toml
   ADMIN_USERNAME = "your-admin"
   ADMIN_PASSWORD = "a-strong-password"
   ```
2. Environment variables `ADMIN_USERNAME` and `ADMIN_PASSWORD`.
3. A local `admin_credentials.json` (copy `admin_credentials.example.json`). It is git-ignored.

## Security Notes
- Credentials are not hardcoded or committed; they come from secrets or environment variables.
- Employee face embeddings and attendance logs stay local and are excluded from version control.
- Only recognized employees can submit attendance.
- Attendance is location-restricted for added security.

## Usage
- **Admin**: Log in with credentials, add/remove employees, and download attendance.
- **Employee**: Go to the Attendance page, take a photo, and submit attendance if recognized and at the correct location.

## Requirements
See `requirements.txt` for all dependencies.

---
Developed for secure, location-based employee attendance using facial recognition.

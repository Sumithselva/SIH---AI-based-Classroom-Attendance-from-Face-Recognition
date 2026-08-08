# SIH-AI-based-Classroom-Attendance-from-Face-Recognition

# AI-Based Classroom Attendance Using Face Recognition

## Problem Statement

Manual classroom attendance is a time-consuming and repetitive process. In large classrooms, teachers may spend several minutes taking attendance, which reduces valuable teaching time. Manual attendance can also lead to errors such as incorrect marking, proxy attendance, duplicate entries, and difficulty in maintaining long-term attendance records.

Existing attendance methods such as roll calls, paper-based registers, and manual spreadsheet entry require continuous human effort and are difficult to manage efficiently across multiple classes and dates.

The challenge is to develop an **AI-based automated classroom attendance system** that can identify registered students from a classroom image or live camera feed and automatically generate their attendance records.

The proposed system should be accurate, easy to use, secure, and provide teachers with the ability to verify and correct attendance before storing the final record.

---



## System Workflow

```text
              ┌──────────────────────┐
              │   Teacher / Admin    │
              └──────────┬───────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │ Student Registration │
              │  Face Data + Details │
              └──────────┬───────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │ Face Database /      │
              │ Student Database     │
              └──────────────────────┘
                         ▲
                         │
                         │ Comparison
                         │
┌────────────────────────┴────────────────────────┐
│                                                 │
▼                                                 ▼
┌──────────────────┐                    ┌──────────────────┐
│ Live Camera Feed │                    │ Classroom Image  │
└────────┬─────────┘                    └────────┬─────────┘
         │                                       │
         └────────────────┬──────────────────────┘
                          ▼
                ┌────────────────────┐
                │   Face Detection   │
                └─────────┬──────────┘
                          ▼
                ┌────────────────────┐
                │  Face Recognition  │
                └─────────┬──────────┘
                          ▼
                ┌────────────────────┐
                │ Match with Student │
                │      Database      │
                └─────────┬──────────┘
                          ▼
                ┌────────────────────┐
                │ Present / Absent   │
                └─────────┬──────────┘
                          ▼
                ┌────────────────────┐
                │ Attendance Database│
                └─────────┬──────────┘
                          ▼
                ┌────────────────────┐
                │ Teacher Dashboard  │
                └─────────┬──────────┘
                          ▼
                ┌────────────────────┐
                │ CSV Report Export  │
                └────────────────────┘
```

---

## System Architecture

The system consists of four major layers:

### 1. Input Layer

The system accepts either:

* Live camera feed
* Uploaded classroom photograph

The input is processed to identify all visible faces.

### 2. AI Processing Layer

The AI module performs:

```text
Image / Video
      ↓
Face Detection
      ↓
Face Alignment / Preprocessing
      ↓
Face Feature Extraction
      ↓
Face Matching
      ↓
Student Identification
```

The extracted facial features are compared with the registered student database to determine the identity of each detected student.

### 3. Application Layer

The application layer handles:

* Attendance generation
* Present/Absent calculation
* Teacher verification
* Attendance correction
* Search and filtering
* Report generation

### 4. Database Layer

The database maintains:

```text
Student Information
        +
Face Data / Embeddings
        +
Attendance Records
        +
Class Information
```

---

## Expected Technology Stack

### Frontend

* HTML
* CSS
* JavaScript
* React.js (optional)

### Backend

* Python
* Flask / FastAPI

### AI / Machine Learning

* OpenCV
* Face detection model
* Face recognition / face embedding model
* NumPy
* Scikit-learn

### Database

* SQLite for prototype
* MySQL / PostgreSQL for deployment

### Reporting

* Python CSV module / Pandas

### Development Tools

* Git
* GitHub
* VS Code

---

## Database Design

### Student Table

| Field          | Description                    |
| -------------- | ------------------------------ |
| student_id     | Unique student identifier      |
| name           | Student name                   |
| department     | Student department             |
| year           | Academic year                  |
| section        | Class section                  |
| face_embedding | Registered face representation |

### Attendance Table

| Field         | Description              |
| ------------- | ------------------------ |
| attendance_id | Unique attendance record |
| student_id    | Student identifier       |
| date          | Attendance date          |
| time          | Attendance time          |
| status        | Present / Absent         |
| confidence    | Recognition confidence   |

---

## Attendance Algorithm

```text
1. Start attendance session.
2. Capture classroom image or camera frame.
3. Detect all faces.
4. Preprocess detected faces.
5. Generate face embeddings.
6. Compare embeddings with registered students.
7. Identify matching students.
8. Mark matched students as Present.
9. Mark undetected registered students as Absent.
10. Display results to teacher.
11. Allow teacher to verify/correct attendance.
12. Store final attendance in database.
13. Generate CSV report if required.
```

---

## Advantages

* Reduces time required for manual attendance
* Minimizes manual data-entry errors
* Supports multiple faces in a single classroom image
* Provides centralized attendance records
* Allows teacher verification
* Enables CSV report generation
* Reduces paperwork
* Provides a scalable foundation for educational institutions

---

## Accuracy Evaluation

The system will be evaluated using a labeled dataset containing registered student face images and classroom attendance images.

Important evaluation metrics include:

### Face Recognition Accuracy

Measures how correctly the system identifies registered students.

```text
Recognition Accuracy =
Correctly Recognized Faces / Total Tested Faces × 100
```

### False Recognition Rate

Measures how often a face is incorrectly identified as another student.

### False Rejection Rate

Measures how often a registered student is not correctly recognized.

### Attendance Accuracy

Measures the correctness of the final Present/Absent attendance record.

The final project report will include the experimental dataset size, testing conditions, recognition accuracy, and other evaluation results obtained during implementation.

---

## Privacy and Security

Since the system processes facial data, privacy and responsible handling of biometric information are important.

The system should:

* Obtain appropriate consent before collecting student face data.
* Restrict access to authorized teachers/admins.
* Avoid exposing raw facial images unnecessarily.
* Protect stored face representations and attendance records.
* Provide appropriate data deletion/retention controls.
* Use the system only for legitimate educational attendance purposes.

---

## Future Enhancements

The proposed system can be extended with:

* Mobile application for teachers
* Real-time attendance using IP/CCTV cameras
* Liveness detection
* Mask/partial-face recognition support
* Multi-class and multi-section management
* Cloud-based attendance storage
* Automated attendance analytics
* Parent/student attendance portal
* Low-confidence recognition alerts
* Integration with existing college ERP systems

---

## Expected Outcome

The final system will provide a functional AI-powered attendance platform capable of:

**Registering students → Detecting faces → Recognizing students → Generating Present/Absent status → Teacher verification → Database storage → CSV report generation**

The solution aims to make classroom attendance **faster, more reliable, easier to manage, and less dependent on manual processes**.

---



## Conclusion

The **AI-Based Classroom Attendance System using Face Recognition** provides an automated alternative to traditional attendance methods. By combining computer vision, face recognition, database management, and a teacher dashboard, the system can significantly reduce the effort required to record classroom attendance.

The teacher remains responsible for verifying the generated attendance, making the system practical for real-world educational environments while reducing repetitive manual work.

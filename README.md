# ALT_School_MongoDB_Exam
# EduHub MongoDB Project
# Overview
This project showcases a complete NoSQL database backend for EduHub, an online e-learning platform, using MongoDB. It simulates a real-world application involving course management, user registration, enrollment, assessments, and analytics. It demonstrates skills in data modeling, CRUD operations, aggregation, indexing, validation, and performance optimization using Python (PyMongo) and MongoDB Compass.

# Project Features
 Functional Modules
User Management: Student/instructor registration, authentication, and profile updates.

Course Management: Course creation, publishing, categorization, and organization of lessons.

Enrollment System: Student enrollments, progress tracking, and completion status.

Assessment System: Assignment creation, submissions, grading, and feedback.

Analytics & Reporting: Enrollment stats, revenue tracking, performance metrics.

Search & Discovery: Case-insensitive, filterable course search functionality.

 Tech Stack
Database: MongoDB v8.0+ (hosted on MongoDB Atlas)

Interface: MongoDB Compass, MongoDB Shell

Language: Python 3.x

Libraries:

pymongo – MongoDB operations

pandas – Data manipulation

faker – Sample data generation

datetime – Time-based queries

# Database Schema
1. users
Holds data for students and instructors.

Fields: userId, email, firstName, lastName, role, profile, dateJoined, isActive

2. courses
Contains course details.

Fields: courseId, title, instructorId, description, category, tags, price, level, createdAt, isPublished

3. enrollments
Tracks student registrations to courses.

Fields: enrollmentId, studentId, courseId, enrollmentDate, completionStatus

4. lessons
Stores course lessons.

Fields: lessonId, courseId, title, content, videoUrl, order, createdAt

5. assignments
Holds assignment details for each course.

Fields: assignmentId, courseId, title, description, dueDate

6. submissions
Tracks assignment submissions and grades.

Fields: submissionId, assignmentId, studentId, submittedAt, grade, feedback

# users Collection Schema

| Field        | Type    | Description                         |
|--------------|---------|-------------------------------------|
| userId       | String  | Unique user identifier              |
| email        | String  | Must be unique and required         |
| role         | String  | Enum: 'student' or 'instructor'     |
| dateJoined   | Date    | Timestamp of registration           |
| isActive     | Boolean | User activation status              |
| profile.bio  | String  | User bio                            |
| profile.skills | Array | List of skills                      |

# CRUD Operations
CRUD scripts cover:

User registration

Course creation and publishing

Enrollments and lesson addition

Profile and grade updates

Soft deletes and enrollment removals

# Aggregation & Analytics
Custom aggregation pipelines provide:

Course popularity

Student performance and completion rate

Instructor-level analytics (revenue, average rating)

Monthly trends and engagement insights

# Indexing & Optimization
Indexes added for fast queries on email, courseId, assignmentId, etc.

Used .explain() to evaluate performance before/after optimization.

Query time improvements documented with code timing.

# Data Validation & Error Handling
Schema validation rules implemented for required fields and formats.

Duplicate inserts, missing values, and enum mismatches are handled gracefully.

Validation errors tested and resolved using MongoDB’s $jsonSchema.

# Project Structure
bash
Copy
Edit
eduhub/
│
├── eduhub_mongodb_project.ipynb     # Interactive notebook with all queries
├── eduhub_queries.py                # Python script for all CRUD & Aggregation
├── sample_data/
│   ├── users.json
│   ├── courses.json
│   └── ... (other collections)
├── README.md                        # Project documentation
└── test_results.md                  # Output of test queries
 Setup Instructions
Install Dependencies:

bash
Copy
Edit
pip install pymongo pandas faker
Clone & Connect:

Connect your MongoDB Atlas URI in your Python scripts or notebook.

Import or run scripts from eduhub_queries.py.

Run Notebook:
Launch eduhub_mongodb_project.ipynb to follow all queries step-by-step.

# Challenges & Solutions
Challenge	Solution
Handling missing fields during validation	Applied $jsonSchema and updated sample data
Query slowness on large lookups	Added indexes and optimized aggregation pipelines
Referential consistency	Enforced by application-level code logic

# Learning Outcomes
NoSQL database design and relationships

PyMongo operations and aggregation

Indexing and query optimization

Schema validation and production-level error handling


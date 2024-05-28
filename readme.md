# Student Management System using Java Swing

## Overview

The Student Management System is a Java-based GUI application designed to manage student information, enroll students in courses, assign grades, and display student performance. The application provides a user-friendly interface for administrators to manage student data efficiently.

## Features

- **Student Management**: Add, update, and delete student information.
- **Course Enrollment**: Enroll students in courses and manage their enrollments.
- **Grade Management**: Assign grades to students for their enrolled courses.
- **Display Grades**: View student grades and calculate average grades.
- **User-Friendly Interface**: Easy-to-use GUI with intuitive navigation and functionality.

## Requirements

- Java Development Kit (JDK) 8 or higher
- NetBeans IDE (recommended) or any other Java IDE

## Installation and Setup

1. **Clone the Repository**: 
   ```sh
   git clone https://github.com/yourusername/StudentManagementSystem.git
   ```

2. **Open the Project**:
   - Open NetBeans IDE.
   - Click on `File` -> `Open Project`.
   - Select the `StudentManagementSystem` folder.

3. **Build the Project**:
   - Right-click on the project in the Projects tab.
   - Select `Clean and Build`.

4. **Run the Project**:
   - Right-click on the project in the Projects tab.
   - Select `Run`.

## Usage

### Main Panels

1. **Student Management Panel**:
   - **Add Student**: Enter student details and click `Add`.
   - **Update Student**: Select a student from the list, update details, and click `Update`.
   - **Delete Student**: Select a student from the list and click `Delete`.

2. **Course Enrollment Panel**:
   - **Enroll Student**: Select a student and a course, then click `Enroll`.
   - **View Enrollments**: View the list of enrolled students and their courses.

3. **Grade Management Panel**:
   - **Assign Grade**: Select a student, select a course, enter a grade, and click `Assign Grade`.
   - **View Grades**: View the list of students, their courses, and assigned grades.

4. **Display Grades**:
   - **View Average Grades**: View the average grade of each student.

### Event Handling

- **Button Click Events**: Each button in the GUI is associated with an event handler that performs specific actions, such as adding a student, enrolling in a course, or assigning a grade.
- **List Selection Events**: Actions such as populating the course list when a student is selected are handled through list selection events.

## Code Structure

- **Main Class**: `StudentManagementApp.java`
- **Student Management**: `StudentManagementPanel.java`
- **Course Enrollment**: `CourseEnrollmentPanel.java`
- **Grade Management**: `GradeManagementPanel.java`
- **Display Grades**: `DisplayGradesPanel.java`

### Key Methods

- **populateStudentDropdown()**: Populates the student dropdown list.
- **enrollStudent()**: Enrolls a student in a selected course.
- **assignGrade()**: Assigns a grade to a student for a selected course.
- **showTableData()**: Displays the student, courses, and average grades in a table.

### Sample Method: Assign Grade

```java
   private void assignGrade() {
        String student = (String) gradeStudentlist.getSelectedItem();
        String studentId = student.split(":")[0];//Retrive student ID
        String subject = (String) gradeCourseSelected.getSelectedItem();
        String grade = gradeField.getText();

        if (studentId != null && subject != null && !grade.isEmpty()) {            
            if(Double.parseDouble(grade)>= 0 && Double.parseDouble(grade) <= 4.0) {
                studentGrades.putIfAbsent(studentId, new HashMap<>());
                Map<String, String> subjectGrades = studentGrades.get(studentId);
                subjectGrades.put(subject, grade);
                studentGrades.put(studentId, subjectGrades);
                JOptionPane.showMessageDialog(this, "Grade assigned successfully!");
                gradeField.setText("");
            }else {
                JOptionPane.showMessageDialog(this, "Grade must be >= 0 or <=4.0");
            }
            
        } else {
            JOptionPane.showMessageDialog(this, "Please select a student, subject and enter a grade.");
        }
    }
```

## Contributing

- **Fork the Repository**: Fork this repository to your own GitHub account.
- **Create a Branch**: Create a new branch for your feature or bug fix.
- **Commit Changes**: Make your changes and commit them with descriptive messages.
- **Push to Branch**: Push your changes to the branch on your forked repository.
- **Create a Pull Request**: Open a pull request to merge your changes into the main repository.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgements

- Java Swing for GUI components
- NetBeans IDE for development environment

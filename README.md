#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Course {
public:
    int courseID;
    string courseName;

    Course(int id, string name) : courseID(id), courseName(name) {}
};

class Student {
public:
    int studentID;
    string name;
    vector<Course> courses;

    Student(int id, string studentName) : studentID(id), name(studentName) {}

    void enrollCourse(Course course) {
        courses.push_back(course);
    }

    void displayInfo() {
        cout << "Student ID: " << studentID << ", Name: " << name << endl;
        cout << "Enrolled Courses: " << endl;
        for (Course c : courses) {
            cout << "  - " << c.courseName << " (ID: " << c.courseID << ")" << endl;
        }
    }
};

class Professor {
public:
    int profID;
    string name;
    vector<Course> courses;

    Professor(int id, string profName) : profID(id), name(profName) {}

    void assignCourse(Course course) {
        courses.push_back(course);
    }

    void displayInfo() {
        cout << "Professor ID: " << profID << ", Name: " << name << endl;
        cout << "Assigned Courses: " << endl;
        for (Course c : courses) {
            cout << "  - " << c.courseName << " (ID: " << c.courseID << ")" << endl;
        }
    }
};

int main() {
    Course math(101, "Mathematics");
    Course cs(102, "Computer Science");
    
    Student s1(1, "Ahmed Ali");
    s1.enrollCourse(math);
    s1.enrollCourse(cs);
    
    Professor p1(201, "Dr. Hassan");
    p1.assignCourse(math);
    p1.assignCourse(cs);
    
    cout << "--- Student Information ---" << endl;
    s1.displayInfo();
    
    cout << "\n--- Professor Information ---" << endl;
    p1.displayInfo();
    
    return 0;
}

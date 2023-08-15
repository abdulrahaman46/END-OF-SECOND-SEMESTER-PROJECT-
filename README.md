# END-OF-SECOND-SEMESTER-PROJECT-
UEB3263322/ABDUL RAHAMAN 

#include <iostream>
#include <vector>
#include <string>
#include <ctime>
#include <cstdlib> // For rand() and srand()
#include <algorithm> // For std::shuffle
#include <random> // For random number generation

class Question {
public:
    std::string text;
    std::vector<std::string> options;
    int correctOption;
    int score;
    std::string comment;
};

class Exam {
public:
    std::string title;
    std::vector<Question> questions;
    time_t startTime;
    time_t endTime;
    int timer;
    int totalScore;
    bool isPublished; // Added result status

    void displayQuestions();
    void takeExam();
    void gradeExam();
    void publishResults(); // Added function to publish results
};

// Function to display exam questions
void Exam::displayQuestions() {
    // Code to display questions and options
}

// Function to take the exam
void Exam::takeExam() {
    // Code to record student's answers and time taken
}

// Function to grade the exam
void Exam::gradeExam() {
    // Code to calculate marks and display results
    // Set isPublished = false after grading
    isPublished = false;
}

// Function to publish the results
void Exam::publishResults() {
    // Code to publish the results to students
    isPublished = true;
    std::cout << "Results published!" << std::endl;
}

// Function to create an exam and randomly select questions from a pool
Exam createExam(std::vector<Question>& questionPool, int numQuestions) {
    Exam exam;
    exam.questions.resize(numQuestions);
    
    // Check if the question pool has enough questions for the exam
    if (questionPool.size() < static_cast<size_t>(numQuestions)) {
        std::cout << "Not enough questions in the pool for the exam." << std::endl;
        return exam;
    }
    
    // Randomly select questions from the pool
    std::random_device rd;
    std::mt19937 g(rd());
    std::shuffle(questionPool.begin(), questionPool.end(), g);
    
    for (int i = 0; i < numQuestions; ++i) {
        exam.questions[i] = questionPool[i];
    }

    // Code to set exam details, add questions, and set up timer
    exam.isPublished = false;
    return exam;
}

int main() {
    bool isAdmin = true; // Example role, modify as needed
    
    // For administrators:
    if (isAdmin) {
        // Code to create and manage exams, publish results, etc.
        
        // Sample question pool
        std::vector<Question> questionPool = {
            // Add your pool of questions here
        };
        
        int numQuestions = 5; // Set the number of questions for the exam
        
        // Create an exam with randomly selected questions from the pool
        Exam exam = createExam(questionPool, numQuestions);
        
        // Sample code to leave comments on exam questions
        for (Question& question : exam.questions) {
            std::cout << "Enter comment for Question: " << question.text << std::endl;
            std::getline(std::cin, question.comment);
        }
        
        // Grade the exam and publish results
        exam.gradeExam();
        exam.publishResults();
    }
    
    // For students:
    else {
        // Code to display available exams, allow them to take exams, and view results.
    }

    return 0;
}

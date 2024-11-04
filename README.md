# CSC385
***************************************************
Project 2—The Sleeping Teaching Assistant
***************************************************
A university computer science department has a teaching assistant (TA) who
helps undergraduate students with their programming assignments during
regular office hours. The TA’s office is rather small and has room for only one
desk with a chair and computer. There are three chairs in the hallway outside
the office where students can sit and wait if the TA is currently helping another
student. When there are no students who need help during office hours, the
TA sits at the desk and takes a nap. If a student arrives during office hours
and finds the TA sleeping, the student must awaken the TA to ask for help. If a
student arrives and finds the TA currently helping another student, the student
sits on one of the chairs in the hallway and waits. If no chairs are available, the
student will come back at a later time.
Using POSIX threads, mutex locks, and semaphores, implement a solution
that coordinates the activities of the TA and the students. Details for this
assignment are provided below.

***************************************************
The Students and the TA
***************************************************

Using Pthreads (Section 4.4.1), begin by creating n students where each student
will run as a separate thread. The TA will run as a separate thread as well.
Student threads will alternate between programming for a period of time and
seeking help from the TA. If the TA is available, they will obtain help.Otherwise,
they will either sit in a chair in the hallway or, if no chairs are available, will
resume programming and will seek help at a later time. If a student arrives
and notices that the TA is sleeping, the student must notify the TA using a
semaphore. When the TA finishes helping a student, the TA must check to see
if there are students waiting for help in the hallway. If so, the TA must help
each of these students in turn. If no students are present, the TA may return to
napping.
Perhaps the best option for simulating students programming—as well as
the TA providing help to a student—is to have the appropriate threads sleep
for a random period of time.
Coverage of POSIX mutex locks and semaphores is provided in Section 7.3.
Consult that section for details.
***************************************************
An online C compiler that supports threading can be used to run the code: https://www.jdoodle.com/c-online-compiler
***************************************************



# Sleeping-TA-Assignment
Sleeping Teaching Assistant

This project simulates the "Sleeping Teaching Assistant" problem, a classic multithreading and synchronization problem. Using POSIX threads, mutexes, and semaphores, this program models a teaching assistant (TA) helping students in a small office with limited seating. The TA sleeps when no students are waiting and helps each student in turn when they arrive.
Table of Contents

    Problem Description
    Key Concepts
    Features
    Project Structure
    Setup and Compilation
    Usage
    Example Output
    Notes
    License

Problem Description

A university TA helps students with programming assignments during regular office hours. The TA's office can only fit one desk, and there are three chairs outside the office where students can wait. Here’s how the simulation works:

    If no students are waiting, the TA sleeps at the desk.
    When a student arrives and finds the TA sleeping, they wake up the TA for assistance.
    If the TA is busy helping another student and there are available chairs, the student waits.
    If no chairs are available, the student leaves and returns later.

This project uses POSIX threads to simulate multiple students and a TA working concurrently, employing semaphores and mutex locks to manage synchronization and prevent race conditions.
Key Concepts

This project reinforces the following concepts:

    Multithreading with POSIX threads (pthread library)
    Synchronization with mutexes and semaphores
    Classical Synchronization Problems: Modeled after the "Sleeping Barber" problem, a common scenario in operating systems coursework.
    Concurrency Control in resource-limited environments

Features

    Simulates multiple students who periodically seek help from the TA.
    Implements the TA as a thread that alternates between napping and helping students.
    Uses semaphores and mutexes to handle student-TA interactions and manage shared resources safely.
    Randomized sleep times to simulate realistic programming and helping times.

Project Structure

    sleeping_ta.c: Contains the main code for the TA-student simulation.
    README.md: Project documentation.
    Makefile (optional): Can be included to automate compilation.

Setup and Compilation
Prerequisites

    gcc: This project uses gcc for compiling C code. Ensure it is installed on your machine.
    POSIX Threads (pthread): This project relies on pthread, available on most Unix-like systems (Linux, macOS). On Windows, POSIX compatibility libraries like Cygwin or MinGW are required.

Compilation

To compile the code, use the following command in your terminal:

bash

gcc -pthread sleeping_ta.c -o sleeping_ta

This will create an executable named sleeping_ta.
Usage

To run the simulation:

bash

gcc -pthread sleeping_ta.c -o sleeping_ta

This will create an executable named sleeping_ta.

Usage

To run the simulation:

bash

./sleeping_ta

The program will run indefinitely, simulating the TA helping students. 
To stop it, use Ctrl+C.


Example Output

The following is an example of what you might see in the terminal:

Student 1 is programming.
Student 2 is programming.
Student 1 is waiting for the TA. Students waiting: 1
TA is helping a student. Students waiting: 0
Student 3 is programming.
Student 2 is waiting for the TA. Students waiting: 1
Student 4 is programming.
TA is helping a student. Students waiting: 0
...

In this output:

    Student X is programming: The student is working on their assignment.
    Student X is waiting for the TA: The student is waiting in line.
    TA is helping a student: The TA is assisting a student.
Notes

    Infinite Simulation: The simulation runs indefinitely to simulate ongoing office hours. Use Ctrl+C to terminate.
    Adjustable Parameters: You can modify NUM_STUDENTS and NUM_CHAIRS in the code to simulate different scenarios.
    Concurrency Control: Mutexes and semaphores prevent race conditions and ensure only one student is assisted at a time



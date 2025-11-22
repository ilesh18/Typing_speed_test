Typing Speed Test
Overview of the Project
This is a command-line Python application designed to test and improve typing speed and accuracy. Users can participate in standard typing tests or timed challenges, track their progress over time, unlock achievements, and visualize improvements through graphs. All data is stored in a MySQL database for persistence across sessions. The app is ideal for individuals looking to practice typing skills, with features inspired by popular typing test tools.

Features
Typing Test Mode: Complete 5 random sentences, calculate average WPM (Words Per Minute), track errors, and save results.
Typing Challenge Mode: Choose difficulty levels (Easy: 60s, Medium: 45s, Hard: 30s) and type within a time limit.
Achievements System: Unlock badges for milestones like reaching 60+ WPM, perfect accuracy, or completing multiple tests.
Progress Tracking: View historical results and plot the last 5 attempts using Matplotlib.
Database Persistence: Store user results and achievements in MySQL for long-term tracking.
Error Analysis: Uses sequence matching to detect and report incorrect words.
User-Friendly Menu: Simple CLI interface with options to start tests, view data, or exit.
Technologies/Tools Used
Programming Language: Python 3.7+
Database: MySQL (for data storage and retrieval)
Libraries:
mysql-connector-python: For MySQL database connections.
matplotlib: For generating progress plots.
difflib: For comparing user input to target sentences (built-in Python library).
getpass, random, time: Built-in Python modules for password input, randomization, and timing.
Other Tools: Command-line interface (no GUI required, but Matplotlib assumes a display for plots).
Steps to Install & Run the Project
Prerequisites
Python 3.7 or higher installed on your system.
MySQL Server installed and running (e.g., via XAMPP, WAMP, or native installation).
A MySQL user with privileges to create databases (default assumed: 'root').
Installation Steps
Clone or Download the Code:

Download the script file (e.g., typing_speed_test.py) to your local machine.
Install Required Python Libraries:

Open a terminal/command prompt and run:

Copy code
pip install mysql-connector-python matplotlib
If you encounter issues, ensure pip is up-to-date: pip install --upgrade pip.
Set Up MySQL:

Start your MySQL server.
Ensure the 'root' user exists and has database creation permissions. If needed, create a new user via MySQL CLI:

Copy code
CREATE USER 'root'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost';
FLUSH PRIVILEGES;
Run the Script:

Navigate to the directory containing typing_speed_test.py.
Execute the script:

Copy code
python typing_speed_test.py
On first run, enter your MySQL root password when prompted. The app will automatically create the database (typing_speed_db) and tables (result and achievements).
Start Using the App:

Follow the on-screen menu to select options (e.g., start a test, view results).
For plotting, ensure your environment supports graphical output (e.g., not a headless server).
Troubleshooting
Connection Errors: Verify MySQL is running and credentials are correct. Check firewall settings.
Library Issues: If matplotlib fails to plot, install additional dependencies (e.g., on Linux: sudo apt-get install python3-tk).
Permissions: Ensure the MySQL user can create databases.
Instructions for Testing
Basic Functionality Test:

Run the app and select "1. Start Typing Test".
Enter a username (e.g., "testuser").
Type the displayed sentences accurately and quickly.
Verify that WPM, time, and errors are calculated and displayed.
Check the database: Log into MySQL and query SELECT * FROM typing_speed_db.result WHERE username='testuser'; to confirm data is saved.
Challenge Mode Test:

Select "2. Typing Challenge".
Choose a difficulty (e.g., Hard: 30s).
Type the sentence within the time limit.
Ensure the app enforces the time limit and saves results only if completed on time.
Achievements Test:

Perform multiple tests to unlock achievements (e.g., reach 60+ WPM for "speedster").
Select "4. View Achievements" and enter the username to verify unlocked badges.
Progress Plot Test:

Complete at least 5 tests for a user.
Select "1. Start Typing Test" again, and check if a plot window appears after completion.
If no plot shows, ensure Matplotlib is configured for your environment.
Edge Case Testing:

Test with empty input, very fast/slow typing, or incorrect usernames.
Simulate DB disconnection (stop MySQL) and verify error handling.
Use tools like unittest for automated tests (e.g., create a test file to mock DB calls and validate WPM calculations).
Performance Test:

Run multiple sessions with different users to ensure DB queries are efficient.
For automated testing, consider adding unit tests to the script (e.g., using Python's unittest module to test functions like calculate_wpm_and_errors).
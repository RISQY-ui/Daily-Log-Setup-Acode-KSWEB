# 📝 Daily Log: Acode + KSWEB Setup & First Vulnerable Web

June 17-18, 2026

---

📋 Table of Contents

· Day 17: Acode + KSWEB Setup
· Day 18: First Vulnerable Web - komi.php

---

Day 17: Acode + KSWEB Setup

Tuesday, June 17, 2026

---

🎯 Goal of the Day

Connect Acode (code editor on phone) with KSWEB (local server on phone) so Faris can edit PHP files directly from the phone.

---

🚀 Setup Steps

1. Open Acode

Open the Acode app on Faris's phone.

2. Open Folder Menu

Tap the folder icon or three lines in the top left corner.

3. Add Path / Folder

Select "Add Path" or "Open Folder", then tap "Select Folder" (or the + icon).

4. Find the htdocs Folder

Navigate to:

```
/storage/emulated/0/htdocs
```

ℹ️ Note: In the phone's file manager, this folder is usually in the root of internal storage (not inside Documents or Download folders).

5. Select & Allow

· Tap "Use this folder"
· Tap "Allow"

---

❓ Why Must Use the htdocs Folder?

Reason Description
KSWEB (Apache) Only reads files inside the htdocs folder
Localhost Access PHP files saved in htdocs can be accessed via localhost:8000
Organized & Clean All web files are stored in one place

---

✅ Next Steps (After Setup)

No Step Description
1 Tap the htdocs folder in Acode Open the folder
2 Select "New File" Create a new file
3 Name it vuln.php or komi.php First PHP file on the phone

---

📊 Day 17 Status

Component Status
Acode Installed ✅
KSWEB Installed ✅
htdocs Folder Found ✅
Acode Connected to htdocs ✅
PHP File Created 🔄 Continued to Day 18

---

Day 18: First Vulnerable Web - komi.php

Thursday, June 18, 2026

---

🎯 Goal of the Day

Create a PHP file named komi.php inside the htdocs folder as Faris's first "vulnerable" website to learn web security.

---

📂 File Created

📍 Location: /storage/emulated/0/htdocs/komi.php

---

📝 Complete Code: komi.php

```php
<?php
// Connect to database
$conn = mysqli_connect("localhost", "root", "");

// Create database & table automatically (for convenience)
mysqli_query($conn, "CREATE DATABASE IF NOT EXISTS test_db");
mysqli_select_db($conn, "test_db");
mysqli_query($conn, "CREATE TABLE IF NOT EXISTS users (id INT, username VARCHAR(50))");
mysqli_query($conn, "INSERT IGNORE INTO users VALUES (1, 'Faris_riski'), (2, 'faris_rizal')");

// --- VULNERABLE PART (SQL Injection) ---
$id = $_GET['id'];
$query = "SELECT * FROM users WHERE id = $id";
$result = mysqli_query($conn, $query);

if ($row = mysqli_fetch_array($result)) {
    echo "<h1>Hello, " . $row['username'] . "!</h1>";
} else {
    echo "Data not found, Darling...";
}
?>
```

---

🔍 Code Explanation

Code Part Function
mysqli_connect("localhost", "root", "") Connect to database on localhost
CREATE DATABASE IF NOT EXISTS test_db Create test_db database if it doesn't exist
CREATE TABLE IF NOT EXISTS users Create users table if it doesn't exist
INSERT IGNORE INTO users VALUES (...) Insert sample data (Faris_riski & faris_rizal)
$id = $_GET['id']; Get id parameter from URL
$query = "SELECT * FROM users WHERE id = $id"; Vulnerable to SQL Injection! Directly inserts input into query
mysqli_fetch_array($result) Fetch and display query result

---

⚠️ Vulnerability

Aspect Description
Type of Flaw SQL Injection (input $id is directly inserted into the query without filtering)
Attack Example localhost:8000/komi.php?id=1 OR 1=1 will display all data

---

🚀 How to Run

Step Action
1 Copy the code above into Acode
2 Save as komi.php in the htdocs folder
3 Open browser on your phone
4 Access: localhost:8000/komi.php?id=1

Expected Output:

URL Result
localhost:8000/komi.php?id=1 Displays "Hello, Faris_riski!"
localhost:8000/komi.php?id=2 Displays "Hello, faris_rizal!"
localhost:8000/komi.php?id=3 Displays "Data not found, Darling..."

---

💡 Lessons Learned Today

Lesson Description
MySQLi How to connect to a database in PHP
GET Parameters Retrieving data from the URL
SQL Injection Security flaw caused by unfiltered input
htdocs Folder Location for web files in KSWEB

---

📊 Day 18 Status

Component Status
komi.php File ✅ Successfully created
test_db Database ✅ Automatically created
users Table ✅ Automatically created
Sample Data ✅ Populated (Faris_riski & faris_rizal)
KSWEB Server ✅ Running on localhost:8000
Browser Output ✅ Displays "Hello, Faris_riski!"

---

✅ FINAL STATUS SUMMARY

Component Status
Acode + KSWEB Setup ✅ Complete
htdocs Folder Connected ✅ Complete
komi.php File Created ✅ Complete
Database & Table Auto-created ✅ Complete
SQL Injection Ready to Learn ✅ Complete

---

🎯 LEARNING CORE

```
Create PHP File → Save in htdocs → Access via localhost:8000 → Learn about security vulnerabilities
```

---

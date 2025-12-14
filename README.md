
## Scam Detector / Suspect Pattern Detector(a.k.a Scam Shield):


## Overview:
Crime is a perasive societal issue in todays world.It necessitates effective and efficient management by all of us.
The Scam Detector is a Java-based desktop application designed to identify scam messages and suspicious URLs using rule-based pattern matching and risk assessment.

---

## Abstract:
Suspect Pattern Detection is a Java-based application that scans textual data for specific patterns associated with suspicious or sensitive content. The system processes input text line by line and identifies occurrences of predefined keywords or phrases.
Each match is recorded along with its location in the text, and a summary report is generated to document the findings. The application operates by comparing input data against a list of suspect patterns and flags any matches found during the scan. 
It is structured to handle plain text files and produce a clear output indicating the presence and frequency of detected patterns. The project focuses on basic text analysis and pattern recognition within a controlled dataset.​
This project offers a foundational approach to automated pattern detection in textual records, providing a streamlined method for identifying potentially critical information.
By reducing manual effort and enhancing consistency in data review, Suspect Pattern Detection contributes to the broader goal of improving investigative efficiency and supporting early identification of crime-related indicators.

--- 
​
The system scans user-provided text or URLs, detects predefined scam indicators (urgency phrases, phishing keywords, suspicious domains, etc.), and classifies the content into **risk levels** such as:

**CRITICAL** – Definite Scam

**HIGH** – Highly Suspicious

**MEDIUM** – Possible Scam

**LOW** – Suspicious

**NO RISK** – Safe Content

This project focuses on clarity, modular design, and explainable detection, making it suitable for academic use and further enhancement.

---

## Features:

* **Text-based Scam Detection** (messages, emails, chat text)
  
* **URL Analysis & Validation**
  
* **Risk Scoring Engine** (Critical / High / Medium / Low / Safe)
 
* **Pattern Matching using Regex**

* **Categorized Scam Patterns** (phishing, urgency, threats, prizes, etc.)

* **Sorting Engine** (by category, detection order, match length)

* **Java Swing GUI (JFrame-based)**

* **Formatted Result Output with Risk Indicators**

---

## Installation / Setup Instructions 
Step 1: Install java 
 Install the java development kit (JDK 8 or above) on your system  
After the installation you can check it by using the following command in the terminal. 
 
Step 2: Open a Java IDE 
Open any Java editor such as NetBeans, IntelliJ IDEA, Eclipse, or VS Code. 
Create a new Java project and add the project source files to it. 
 
Step 3: Add input text file 
Prepare a text file that you want to scan for a suspect pattern. Place this file inside the project folder it will be easy to access  
 
 Step 4: Run the program 
1) Right-click on the main Java file and select Run. 
 2) When the program starts, it will ask for the path of the text file to scan 
 3) Enter the correct path and press Enter. 
   	 
Step 5: View the output 
The program will scan the text line-by-line and display: 
The suspect keywords found 
The line numbers where they appear 
The number of matches detected

---

## USER MANUAL  
STARTING THE APPLICATION: 
        Open the project in your java IDE and run the main file  
         The application will open the in the main terminal 
         
  Providing input:  
       Prepare a plain text file that contains the data to be analyzed 
       When prompted, enter the file path so the system can read the content  
 
 HOW THE SYSTEM WORK’S: 
 The application Read the text file line by line Compare’s each line with the predefined list of suspect keywords, detect and records any matches found 
 
 RESULT: 
After processing, the system displays Which keyword is found on which line it was  found total number of matches, a simple summary report. 
 
ENDING SESSION:  
Once the results are displayed, the user can close the program or run it again with a   different text file. 

---

## System Architecture

The application follows a **modular layered architecture**:

**Main Flow:**

```
User Input → GUI Controller → Pattern Matcher / URL Analyzer
          → Risk Calculator → ScanResult → Result Formatter → Display
```

### Key Modules

* **ScamDetectorGUI** – Main controller & UI handler
* **Pattern Matcher** – Regex-based text scanning
* **URL Detection & Analysis** – Domain and structure validation
* **Risk Calculator** – Assigns final risk level
* **ScanResult (Data Storage)** – Stores matches & summary
* **Sorting Engine** – Organizes detected patterns
* **Display Manager** – Renders formatted output

---

## How the System Works
* User inputs a message or URL

* Text is normalized and scanned using regex-based patterns

* URLs are extracted and analyzed independently

* Each detected indicator is categorized and stored

* A final risk score is calculated

* Results are formatted and displayed to the user

---

## How Detection Works

### Message Scanning

* Input text is normalized (lowercase, trimmed)
* Each line is compared against predefined **SCAM_PATTERNS**
* Regex matching detects keywords and phrases
* Each match is stored with category & context

### URL Verification

* Extracts URLs from text or direct input
* Checks for:

  * Suspicious keywords
  * Multiple subdomains
  * IP-based URLs
  * Fake brand domains
  * URL shorteners

### Risk Assessment Logic

Risk is calculated based on the **number and severity of matches**:

```java
if (matchCount >= 5) return "CRITICAL";
else if (matchCount >= 3) return "HIGH";
else if (matchCount == 2) return "MEDIUM";
else if (matchCount == 1) return "LOW";
else return "NO RISK";
```

---

## Code Snippets
  (For reference)

### Scam Pattern Matching

```java
for (Map.Entry<String, String> entry : SCAM_PATTERNS.entrySet()) {
    Pattern pattern = Pattern.compile(entry.getValue(), Pattern.CASE_INSENSITIVE);
    Matcher matcher = pattern.matcher(message);
    while (matcher.find()) {
        scanResult.addMatch(new Match(entry.getKey(), matcher.group()));
    }
}
```

### URL Analysis

```java
if (url.contains("verify") || url.contains("secure") || domainParts > 3) {
    isSuspicious = true;
}
```

### Merge Sort (By Length)

```java
private void mergeSortByLength(List<Match> list) {
    if (list.size() <= 1) return;
    // recursive divide & merge logic
}
```

---

 ## User Interface Overview

* **Message Input Area** – Paste message text
* **URL Input Field** – Analyze direct links
* **Scan Message Button** – Runs text analysis
* **Check URL Button** – Runs URL analysis
* **Result Panel** – Displays matches & explanations
* **Risk Indicator Label** – Color-coded risk level

Built using **Java Swing (JFrame)**.

---

##  Class Diagram (Core)
Class Diagram Description:

The Scam Detector system is designed using Object-Oriented Programming (OOP) principles and follows a modular class structure. 
The core GUI extends Java Swing components and coordinates with analysis and data classes to detect scams and assess risk.

* `ScamDetectorGUI extends JFrame`
* `ScanResult` contains multiple `Match`
* `Match` optionally links to `URLAnalysis`

**Class Hierarchy Overview**
  
JFrame
  └── ScamDetectorGUI

ScamDetectorGUI extends JFrame, inheriting all Java Swing window functionalities.

**ScamDetectorGUI (Main Controller & UI)**
**Superclass**: JFrame
This is the central controller class responsible for:
Building the user interface
Handling user actions
Coordinating scam detection, URL analysis, sorting, and display

**Attributes**
SCAM_PATTERNS – Static map containing predefined scam keywords & regex patterns
messageArea – Text input area for messages
resultArea – Displays detection results
riskLabel – Shows final risk level
riskPanel – Visual risk indicator panel
sortComboBox – Allows sorting of results
currentResult – Stores the current ScanResult object

**Methods**
scanMessage() – Scans message text for scam patterns
checkURL() – Analyzes a single URL
performScan() – Triggers the complete scan workflow
analyzeURL() – Performs URL risk analysis
mergeSort() – Sorts matches by category
mergeSortByLength() – Sorts matches by text length
displayResults() – Displays formatted output
clearFields() – Resets UI inputs and outputs
ScanResult (Data Storage & Risk Calculation)
Stores all scan-related results and determines the overall risk level.

**Attributes**
matches – List of detected Match objects
riskLevel – Final risk level (CRITICAL / HIGH / MEDIUM / LOW / SAFE)
recommendation – Suggested action for the user
riskColor – UI color mapped to risk level

**Methods**
addMatch() – Adds a detected scam pattern
addURLMatch() – Adds a URL-based detection
calculateRisk() – Computes final risk based on matches
Relationships
Has many Match objects (1 → *)



**Match (Detected Scam Indicator)**
Represents a single detected scam pattern from text or URL.

**Attributes**
category – Type of scam (phishing, urgency, threat, etc.)
text – Matched suspicious content
urlAnalysis – Optional URL analysis result

**Constructors**
Match(String category, String text)
Match(String category, String text, URLAnalysis urlAnalysis)
Relationships
Each Match belongs to one ScanResult
Each Match have URLAnalysis (0..1)



**URLAnalysis (URL Risk Evaluation)**
Handles detection and verification of suspicious URLs.
Attributes
url – The analyzed URL
isSuspicious – Boolean flag
riskLevel – Risk assigned to the URL
reasons – Explanation for why the URL was flagged
Constructor
URLAnalysis(String url)
Usage
Used by ScamDetectorGUI
Optionally linked to Match

**Class Relationships Summary**
Relationship	Description
ScamDetectorGUI → JFrame	Inheritance
ScamDetectorGUI → ScanResult	Contains
ScamDetectorGUI → Match	Contains
ScamDetectorGUI → URLAnalysis	Uses
ScanResult → Match	One-to-Many
Match → URLAnalysis	Optional Association

---


**Design Highlights** 
✔ Encapsulation of detection logic
✔ Separation of UI, logic, and data
✔ Reusable and extensible structure
✔ Easy integration of future modules

--- 

## Technologies Used:
* Java JDK 25 Latest version​
* Java Swing​
* VS Code 

----
## TECHNICAL REQUIREMENTS:​
**Hardware:**
High-performance CPUs or GPUs (e.g., NVIDIA RTX/AI GPUs Intel i7/i9,).​
Memory (RAM): At least 16–32 GB for handling large datasets and real-time analysis. ​
Storage: SSDs with 1 TB+ capacity for storing datasets, logs, and model files. ​
​Networking: Stable internet(120 Mbps or higher). ​



​
​**Software:** 
Operating System:  Windows or Mac or linux.​
​Programming Languages: Java 25 latest LTS version, html.​
​Databases: SQL(Curretly Jawa Swing for temporary data storage)​
​Security Tools: Encryption libraries, access control, and audit logging.(Still under development)

---​
​
## Future Enhancements
**Planned Improvements**

**Real-Time Email Detection:** 
Automatic scanning of incoming emails with instant warnings.
**Multi-Modal Scam Detection:**
Image analysis for fake logos and forged screenshots
QR code scanning
Sender behavior and frequency analysis.
**Browser Extension:**
Real-time website monitoring with visual similarity checks

Future Scope:
Our Scam Detector(ScamSheild) aims to evolve into a comprehensive, real-time scam prevention solution by supporting multi-format detection, advanced URL intelligence, and proactive threat warnings.

---

## Dependencies
This project uses standard Java SE libraries only. No external third-party dependencies are required.

**Core Java Dependencies**
java.awt.* – GUI layout, colors, and event handling
javax.swing.* – JFrame, JPanel, JButton, JTextArea, JLabel, JComboBox
java.util.* – Collections (List, ArrayList, Map, HashMap, LinkedHashMap)
java.util.regex.* – Pattern matching using Pattern and Matcher
java.net.* – URL parsing and validation

**Build & Runtime**
No build tools (Maven/Gradle) required
Compiles and runs using:
javac ScamDetectorGUI.java
java ScamDetectorGUI

---

## Limitations:
Currently, the project only handles text-based content and URL analysis. It cannot analyze images, videos, audio files, or other multimedia content that scammers increasingly use to deceive victims. 
The absence of multi-modal detection capabilities limits the system's effectiveness against modern scams that employ visual deception, fake logos, or manipulated screenshots.
Rule-based detection may produce false positivesCreative or novel scam language may evade patterns.Moreover, new scam types require manual pattern updatesCurrently supports text and URLs only.
No image, video, or audio analysis Performance depends on system resources.

---

## Project Status:


This project is still under development. Current implementation focuses on rule-based detection. More advanced features are yet in development.

---

## Acknowledgements:
Thanks to open-source documentation, developer communities, and educational resources that made this project possible.

---

## Author:
  
  Fathima Qhibtiya Khader
    
    https://github.com/fathimaqhibtiyakhader/JAVA-PROJ 
---

## Contact details:
For feedback, suggestions, or collaboration reach me out at:

**Email**:qhibtitya@gmail.com

---

If you find this project useful, consider starring the repository!

---

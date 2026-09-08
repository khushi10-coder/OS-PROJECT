# 🔐 Intelligent File Backup & Management System

> **A Linux-based intelligent file management system for automated backup, real-time monitoring, duplicate detection, file classification, and AI-based analysis.**

![Linux](https://img.shields.io/badge/OS-Linux-FCC624?logo=linux\&logoColor=black)
![C](https://img.shields.io/badge/Core-C-A8B9CC)
![Python](https://img.shields.io/badge/AI-Python-3776AB)
![SQLite](https://img.shields.io/badge/Database-SQLite-003B57)

---

## 🎯 Project Objective

Build a **local, offline Linux system** that automatically:

* 💾 Performs full and incremental backups
* 👀 Monitors file activity in real time
* 🗂️ Classifies files by type
* ⭐ Prioritizes important project folders
* ♻️ Detects duplicate and redundant files
* 🤖 Uses AI for intelligent backup and anomaly analysis

### Development Phases

```mermaid
flowchart TD
    A["PHASE 1: CORE LINUX SYSTEM<br/>C + Linux + SQLite + inotify"]
    --> B["PHASE 2: AI INTELLIGENCE<br/>Python + ML + Analysis"]
```

---

# 🏗️ System Architecture

```mermaid
flowchart TD
    U["USER"] --> CLI["CLI / MENU"]

    CLI --> CORE["CORE C SYSTEM"]

    CORE --> FM["File Management"]
    CORE --> BE["Backup Engine"]
    CORE --> MON["File Monitoring"]
    CORE --> FC["File Classification"]
    CORE --> DD["Duplicate Detection"]

    FM --> FS["Linux File System"]
    BE --> FS
    MON --> IN["inotify"]
    DD --> SHA["SHA-256"]

    IN --> DB["SQLite"]
    SHA --> DB

    DB --> AI["AI LAYER<br/>Python"]

    AI --> BP["Backup Priority"]
    AI --> AD["Anomaly Detection"]
    AI --> RA["Redundancy Analysis"]
```

---

# ⚙️ Core Modules

| Module                 | Function                                                  |
| ---------------------- | --------------------------------------------------------- |
| 📁 File Manager        | Create, read, write, copy, move and delete files          |
| 💾 Full Backup         | Initial backup of all selected files                      |
| 🔄 Incremental Backup  | Backup only new or modified files                         |
| 👀 Monitoring          | Detect file creation, modification, deletion and movement |
| 🗂️ Classification     | Categorize files by extension                             |
| ⭐ Project Registry     | Mark important folders as high priority                   |
| ♻️ Duplicate Detection | Detect identical files using SHA-256                      |
| 🗄️ SQLite             | Store file and backup metadata                            |
| 🤖 AI Layer            | Analyze backup priority, anomalies and redundancy         |

---

# 💾 Backup Flow

```mermaid
flowchart TD
    A["START"] --> B["Select Source"]
    B --> C["Select Backup Location"]
    C --> D["Full Backup"]
    D --> E["Store Metadata"]
    E --> F["Monitor Changes"]
    F --> G{"New / Modified File?"}
    G -->|YES| H["BACKUP"]
    G -->|NO| I["IGNORE"]
```

### Backup Types

| Type                   | Description                       |
| ---------------------- | --------------------------------- |
| **Full Backup**        | Copies all selected files         |
| **Incremental Backup** | Copies only new or modified files |
| **Restore**            | Recovers files from backup        |

---

# 👀 Real-Time File Monitoring

The system uses Linux **`inotify`** to monitor selected directories.

```mermaid
flowchart LR
    A["File Event"] --> B["inotify"]
    B --> C["C Monitor"]
    C --> D["Backup Decision"]
```

### Monitored Events

```text
CREATE
MODIFY
DELETE
MOVE
```

---

# 🗂️ File Classification

Files are categorized according to their extensions.

| Extension               | Category      |
| ----------------------- | ------------- |
| `.pdf`                  | PDF Document  |
| `.docx`                 | Word Document |
| `.pptx`                 | Presentation  |
| `.xlsx`                 | Spreadsheet   |
| `.jpg`, `.jpeg`, `.png` | Image         |
| `.xml`                  | XML / Data    |
| `.txt`                  | Text          |
| `.c`                    | Source Code   |
| Unknown                 | Other         |

### Classification Flow

```mermaid
flowchart TD
    A["File"] --> B["Read Extension"]
    B --> C{"Known Extension?"}

    C -->|YES| D["Assign Category"]
    C -->|NO| E["Other"]

    D --> F["Store Classification"]
    E --> F
```

---

# ⭐ Project Folder Registry

Users can mark important folders for special treatment.

```text
/home/user/Projects/OS_Project
/home/user/Projects/Final_Year_Project
```

| Setting          | Value   |
| ---------------- | ------- |
| Priority         | HIGH    |
| Backup Frequency | HIGH    |
| Monitoring       | ENABLED |

---

# ♻️ Duplicate Detection

Exact duplicate files are detected using **SHA-256 hashes**.

```mermaid
flowchart TD
    A["report.pdf"] --> B["SHA-256 Hash"]
    C["report_copy.pdf"] --> D["SHA-256 Hash"]

    B --> E{"Same Hash?"}
    D --> E

    E -->|YES| F["DUPLICATE DETECTED"]
    E -->|NO| G["Unique File"]

    F --> H["User Decision"]
    H --> I["Keep"]
    H --> J["Delete"]
    H --> K["Quarantine"]
```

> ⚠️ Files are not automatically deleted.

---

# 📏 Rule-Based Backup Decision

Before AI is introduced, predefined rules are used.

```mermaid
flowchart TD
    A["File Event"] --> B{"File Modified?"}

    B -->|YES| C["Add to Backup Queue"]
    B -->|NO| D{"Project Folder?"}

    D -->|YES| E["High Priority"]
    D -->|NO| F{"New File?"}

    F -->|YES| G["Backup"]
    F -->|NO| H["Ignore"]

    C --> I["Backup Decision"]
    E --> I
    G --> I
    H --> I

    I --> J{"Duplicate?"}
    J -->|YES| K["Mark Redundant"]
    J -->|NO| L["Continue"]
```

```text
IF file is modified
        ↓
Add to backup queue

IF file belongs to project folder
        ↓
High priority

IF file is newly created
        ↓
Backup

IF file is unchanged
        ↓
Ignore

IF duplicate detected
        ↓
Mark redundant
```

---

# 🤖 AI Layer

The AI layer is added after the core system is functional.

```mermaid
flowchart TD
    A["Linux"] --> B["File Events"]
    B --> C["C System"]
    C --> D["SQLite"]
    D --> E["Python AI"]

    E --> F["Backup Priority"]
    E --> G["Anomaly Detection"]
    E --> H["Redundancy Analysis"]
```

### AI Features

| Feature                | Purpose                              |
| ---------------------- | ------------------------------------ |
| 🧠 Backup Priority     | Identify important files             |
| 🚨 Anomaly Detection   | Detect unusual file activity         |
| ♻️ Redundancy Analysis | Identify potentially redundant files |

---

# 🧠 Intelligent Backup Priority

AI analyzes:

* File access frequency
* Modification frequency
* Last usage
* Project-folder status
* File type
* Previous backup history

### Example

```text
main.c

Access Count: 100
Modification Count: 40
Project Folder: YES

Result:
Importance = HIGH
Backup Priority = HIGH
```

---

# 🚨 Anomaly Detection

### Normal Activity

```text
20–30 files/day
Normal access hours
Regular file modifications
```

### Unusual Activity

```text
Hundreds of files modified rapidly
Large number of file changes
Unusual activity pattern
```

```mermaid
flowchart TD
    A["File Activity"] --> B["Collect Activity Data"]
    B --> C["Python AI"]
    C --> D{"Activity Pattern"}

    D -->|Normal| E["NORMAL"]
    D -->|Unusual| F["SUSPICIOUS ACTIVITY"]
```

Output:

```text
NORMAL
   OR
SUSPICIOUS ACTIVITY
```

---

# ♻️ Smart Redundancy Analysis

AI can analyze:

```text
Similar file names
Usage frequency
File age
File type
Content similarity (future improvement)
```

Example:

```text
report_final.pdf
report_final_copy.pdf
report_final_v2.pdf
```

These files can be flagged as **potentially redundant** for user review.

```mermaid
flowchart TD
    A["Files"] --> B["Analyze Metadata"]
    B --> C["File Names"]
    B --> D["Usage Frequency"]
    B --> E["File Age"]
    B --> F["File Type"]
    B --> G["Content Similarity"]

    C --> H["Redundancy Analysis"]
    D --> H
    E --> H
    F --> H
    G --> H

    H --> I["Potentially Redundant"]
    I --> J["User Review"]
```

---

# 🛠️ Technology Stack

| Component         | Technology                 |
| ----------------- | -------------------------- |
| Operating System  | Linux / Ubuntu             |
| Core Language     | C                          |
| Linux Integration | POSIX / Linux System Calls |
| File Monitoring   | inotify                    |
| Database          | SQLite                     |
| Hashing           | SHA-256                    |
| AI Language       | Python                     |
| Machine Learning  | Scikit-learn               |
| Data Processing   | Pandas / NumPy             |
| Interface         | Command Line               |
| Version Control   | Git / GitHub               |

---

# 📂 Project Structure

```text
intelligent-file-backup-system/
│
├── src/
│   ├── main.c
│   ├── file_manager/
│   ├── backup/
│   ├── monitoring/
│   └── redundancy/
│
├── database/
│   ├── schema.sql
│   └── system.db
│
├── ai/
│   ├── backup_priority.py
│   ├── anomaly_detection.py
│   └── redundancy_analysis.py
│
├── backups/
├── test_files/
│
├── README.md
└── Makefile
```

### Architecture Overview

```mermaid
flowchart TD
    ROOT["intelligent-file-backup-system"]

    ROOT --> SRC["src/"]
    SRC --> MAIN["main.c"]
    SRC --> FM["file_manager/"]
    SRC --> BACKUP["backup/"]
    SRC --> MON["monitoring/"]
    SRC --> RED["redundancy/"]

    ROOT --> DB["database/"]
    DB --> SCHEMA["schema.sql"]
    DB --> SYSTEM["system.db"]

    ROOT --> AI["ai/"]
    AI --> BP["backup_priority.py"]
    AI --> AD["anomaly_detection.py"]
    AI --> RA["redundancy_analysis.py"]

    ROOT --> BACKUPS["backups/"]
    ROOT --> TEST["test_files/"]
    ROOT --> README["README.md"]
    ROOT --> MAKE["Makefile"]
```

---

# 📊 Evaluation Metrics

| Metric         | Objective                |
| -------------- | ------------------------ |
| Backup Size    | Reduce storage           |
| Backup Time    | Reduce backup time       |
| Restore Time   | Enable fast recovery     |
| I/O Overhead   | Minimize unnecessary I/O |
| Detection Rate | Detect unusual behavior  |

### Full vs Incremental Backup

| Feature      | Full Backup | Incremental Backup |
| ------------ | ----------- | ------------------ |
| Files Copied | All         | New / Modified     |
| Storage      | High        | Low                |
| Time         | High        | Lower              |
| I/O          | High        | Optimized          |

---

# 🔄 Complete System Flow

```mermaid
flowchart TD
    A["USER"] --> B["Configuration"]
    B --> C["Full Backup"]
    C --> D["SQLite Metadata"]
    D --> E["inotify Monitoring"]
    E --> F["File Event"]
    F --> G["Rule Engine"]
    G --> H["AI Analysis"]

    H --> I["BACKUP"]
    H --> J["QUEUE"]
    H --> K["IGNORE"]
    H --> L["ALERT"]

    I --> M["Database Update"]
    J --> M
    K --> M
    L --> M
```

```text
USER
 │
 ▼
Configuration
 │
 ▼
Full Backup
 │
 ▼
SQLite Metadata
 │
 ▼
inotify Monitoring
 │
 ▼
File Event
 │
 ▼
Rule Engine
 │
 ▼
AI Analysis
 │
 ├──→ BACKUP
 ├──→ QUEUE
 ├──→ IGNORE
 └──→ ALERT
 │
 ▼
Database Update
```

---

# 🔗 Overall System Pipeline

```mermaid
flowchart LR
    A["User"] --> B["Linux File System"]
    B --> C["inotify"]
    C --> D["C Core System"]
    D --> E["Rule Engine"]
    E --> F["SQLite"]

    F --> G["Python AI"]

    G --> H["Backup Priority"]
    G --> I["Anomaly Detection"]
    G --> J["Redundancy Analysis"]

    H --> K["Backup / Queue"]
    I --> L["Alert"]
    J --> M["User Review"]
```

---

# ⭐ Project in One Line

```text
Linux + C + inotify + SQLite + Backup + SHA-256 + AI
                         ↓
          🔐 Intelligent File Management
```

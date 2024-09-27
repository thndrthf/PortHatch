
# PortHatch v1.0 Alpha

**PortHatch v1.0 alpha** is a Python-based tool designed for macOS users to block specified TCP and UDP ports using an intuitive graphical user interface (GUI). Whether you're a developer, network administrator, or security enthusiast, PortHatch offers a straightforward solution to manage port access, enhancing your system's security and control.

---

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Screenshots](#screenshots)
- [Configuration](#configuration)
- [Logging](#logging)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [Acknowledgements](#acknowledgements)

---

## Features

- **User-Friendly GUI:** Easily select and manage ports without diving into command-line complexities.
- **Comprehensive Port List:** Predefined list of common TCP and UDP ports, with the ability to customize.
- **Real-Time Blocking:** Block and unblock ports on-the-fly without restarting your system.
- **Advanced Logging:** Detailed logs of all blocking activities and connection attempts.
- **Log Rotation:** Prevents log files from growing indefinitely by implementing log rotation.
- **Graceful Shutdown:** Ensures all ports are released properly when the application is closed.
- **Daemon Threads:** Background processes that do not interfere with the main application flow.

---

## Prerequisites

Before installing and running PortHatch, ensure you have the following:

- **Operating System:** macOS (tested on macOS Monterey and later)
- **Python:** Python 3.6 or higher
- **Permissions:** Ability to run scripts with `sudo` privileges (required for blocking privileged ports below 1024)

---

## Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/PortHatch.git
   cd PortHatch
   ```

2. **Create a Virtual Environment (Optional but Recommended):**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies:**

   PortHatch primarily uses Python's standard libraries, so no additional packages are required. However, ensure that your Python installation includes `Tkinter` for the GUI.

   - **Verify Tkinter Installation:**

     ```bash
     python3 -m tkinter
     ```

     A simple window should appear if Tkinter is installed correctly.

   - **If Tkinter is Missing:**

     Install Tkinter via Homebrew:

     ```bash
     brew install python-tk
     ```

4. **Download PortHatch:**

   If you haven't cloned the repository, download the `PortHatch.py` script directly from the repository.

---

## Usage

### **Running PortHatch**

1. **Navigate to the Project Directory:**

   ```bash
   cd PortHatch
   ```

2. **Execute the Script:**

   - **For Non-Privileged Ports (Above 1024):**

     ```bash
     python3 PortHatch.py
     ```

   - **For Privileged Ports (Below 1024):**

     Blocking ports below 1024 requires `sudo` privileges.

     ```bash
     sudo python3 PortHatch.py
     ```

     **⚠️ Warning:** Running scripts with `sudo` can pose security risks. Ensure you trust the script and understand its operations before executing it with elevated privileges.

### **Using the GUI**

1. **Select Ports to Block:**

   - Upon launching, a GUI window titled **"PortHatch v1.0 alpha"** will appear.
   - Scroll through the list of ports and select the ones you wish to block by checking the corresponding boxes.

2. **Block Selected Ports:**

   - Click the **"Block Selected Ports"** button.
   - A confirmation message will appear, and the status label will update to **"Status: Blocking Ports"**.

3. **Unblock All Ports:**

   - To release all previously blocked ports, click the **"Unblock All Ports"** button.
   - A confirmation message will appear, and the status label will revert to **"Status: Idle"**.

4. **Graceful Shutdown:**

   - If you attempt to close the GUI window while ports are blocked, a prompt will ask if you want to unblock all ports before quitting.
   - Confirming will ensure all ports are released and the application terminates gracefully.

---

## Configuration

### **Customizing the Port List**

PortHatch comes with a predefined list of common TCP and UDP ports. You can customize this list by modifying the `PORTS` dictionary within the `PortHatch.py` script.

```python
PORTS = {
    22: "SSH (TCP)",
    25: "SMTP (TCP)",
    53: "DNS (TCP/UDP)",
    80: "HTTP (TCP)",
    8080: "HTTP-alt (TCP)",
    # Add or remove ports as needed
}
```

**Recommendation:** For better maintainability, consider moving the port configurations to an external file (e.g., `ports_config.json`) and loading them dynamically.

---

## Logging

PortHatch implements advanced logging to monitor all activities related to port blocking and connection attempts.

### **Log File**

- **Location:** `port_blocker.log` in the project directory.
- **Features:**
  - **RotatingFileHandler:** Prevents the log file from growing indefinitely by rotating logs after they reach 5MB, keeping up to 2 backup files.
  - **Log Format:** Timestamp, log level, and message.

### **Viewing Logs**

You can view the logs using any text editor or via the terminal:

```bash
cat port_blocker.log
```

---

## Contributing

Contributions are welcome! Whether it's reporting bugs, suggesting features, or submitting pull requests, your input helps improve PortHatch.

### **How to Contribute**

1. **Fork the Repository:**

   Click the **"Fork"** button on the repository page to create your own copy.

2. **Clone Your Fork:**

   ```bash
   git clone https://github.com/yourusername/PortHatch.git
   cd PortHatch
   ```

3. **Create a New Branch:**

   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Make Your Changes:**

   Implement your feature or fix.

5. **Commit Your Changes:**

   ```bash
   git add .
   git commit -m "Description of your changes"
   ```

6. **Push to Your Fork:**

   ```bash
   git push origin feature/your-feature-name
   ```

7. **Create a Pull Request:**

   Navigate to the original repository and click **"Compare & pull request"**.

### **Guidelines**

- **Code Quality:** Follow Python's PEP 8 style guidelines.
- **Documentation:** Update the `README.md` and other documentation as necessary.
- **Testing:** Ensure that your changes do not introduce bugs and that existing functionalities remain intact.

---

## License

Distributed under the [MIT License](LICENSE).

---

## Contact

**Your Name**  
Email: [your.email@example.com](mailto:your.email@example.com)  
GitHub: [https://github.com/yourusername](https://github.com/yourusername)

---

## Acknowledgements

- **Python Community:** For providing robust libraries and frameworks.
- **Tkinter Documentation:** For the comprehensive GUI development guide.
- **Open Source Contributors:** For inspiring and sharing their knowledge.

---

## Known Issues

- **Port Release on Shutdown:** Occasionally, ports may remain blocked if the application doesn't terminate gracefully. Ensure to use the **"Unblock All Ports"** button before closing the GUI.
- **Permission Requirements:** Blocking privileged ports (below 1024) requires running the script with `sudo`. Ensure you understand the security implications before doing so.

---

## Future Enhancements

- **Dynamic Port Configuration:** Load port configurations from external files like JSON or YAML.
- **Scheduling:** Allow users to schedule port blocking/unblocking at specific times.
- **Real-Time Monitoring:** Integrate real-time dashboards to visualize port activities.
- **Desktop Notifications:** Inform users about connection attempts or changes in port statuses.
- **Cross-Platform Support:** Extend compatibility to other operating systems like Windows and Linux.

---

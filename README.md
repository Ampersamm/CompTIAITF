# CompTIAITF
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CompTIA ITF+ Practice Exam</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
        }
        .card {
            width: 400px;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
            text-align: center;
        }
        .submit {
            background-color: #28A745;
            color: white;
            padding: 10px;
            width: 100%;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }
        .result {
            margin-top: 10px;
            font-weight: bold;
            color: #000;
        }
    </style>
</head>
<body>
    <h1>CompTIA ITF+ Practice Exam</h1>
    <div class="progress" id="progress">Question 1 of 200</div>
    <div class="card">
        <h2 id="question"></h2>
        <select id="options"></select>
        <button class="submit" onclick="submitAnswer()">Submit</button>
        <div class="result" id="result"></div>
    </div>
    <h2 id="score" style="display: none;"></h2>
    <script>
        const questions = [
    // Module 1 / Unit 1 – Common Computing Devices (20 questions)
    { question: "What is the primary function of a computer?", options: ["To process data", "To store data", "To input data", "To display data"], correctAnswer: 0 },
    { question: "Which of the following best describes the function of the CPU?", options: ["Processes instructions", "Stores data", "Displays images", "Manages network connections"], correctAnswer: 0 },
    { question: "What does RAM stand for?", options: ["Random Access Memory", "Read Access Memory", "Rapid Application Module", "Remote Access Machine"], correctAnswer: 0 },
    { question: "Which device is used to input data into a computer?", options: ["Keyboard", "Monitor", "Printer", "Speaker"], correctAnswer: 0 },
    { question: "Which of the following is considered an output device?", options: ["Keyboard", "Mouse", "Monitor", "Scanner"], correctAnswer: 2 },
    { question: "What is the primary purpose of a server?", options: ["To provide services to other computers", "To play video games", "To edit documents", "To manage personal emails"], correctAnswer: 0 },
    { question: "Which computing device is typically used for mobility?", options: ["Desktop", "Server", "Laptop", "Mainframe"], correctAnswer: 2 },
    { question: "What does IoT stand for?", options: ["Internet of Things", "Information on Technology", "Interface of Tools", "Internal Operating Terminal"], correctAnswer: 0 },
    { question: "Which of the following is an example of an IoT device?", options: ["Smart thermostat", "Desktop computer", "Server", "Laptop"], correctAnswer: 0 },
    { question: "What does BIOS stand for?", options: ["Basic Input Output System", "Binary Integrated Operating System", "Basic Internal Operating Service", "Backup Input Output Sequence"], correctAnswer: 0 },
    { question: "Which component temporarily stores data for quick access?", options: ["RAM", "Hard Disk", "SSD", "CD-ROM"], correctAnswer: 0 },
    { question: "Which type of memory is volatile?", options: ["RAM", "ROM", "SSD", "Flash memory"], correctAnswer: 0 },
    { question: "What is the function of a hard disk drive?", options: ["Permanent data storage", "Temporary data processing", "Input data", "Power supply"], correctAnswer: 0 },
    { question: "Which technology is used for fast storage in modern computers?", options: ["SSD", "HDD", "CD-ROM", "Floppy disk"], correctAnswer: 0 },
    { question: "Which of the following is an example of a mobile computing device?", options: ["Smartphone", "Desktop computer", "Server", "Mainframe"], correctAnswer: 0 },
    { question: "What does GPU stand for?", options: ["Graphics Processing Unit", "General Purpose Unit", "Graphical Performance Utility", "Gaming Processing Unit"], correctAnswer: 0 },
    { question: "Which of the following is a characteristic of a laptop?", options: ["Portable", "Stationary", "Requires external power always", "Only for gaming"], correctAnswer: 0 },
    { question: "Which company is known for producing Macintosh computers?", options: ["Apple", "Dell", "HP", "Lenovo"], correctAnswer: 0 },
    { question: "Which of the following best describes a desktop computer?", options: ["A stationary computer designed for use on a desk", "A portable device", "A wearable device", "A server rack component"], correctAnswer: 0 },
    { question: "What is the role of peripheral devices in a computer system?", options: ["They provide input and output functions", "They process data", "They store software", "They manage the operating system"], correctAnswer: 0 },

    // Module 1 / Unit 2 – Using a Workstation (15 questions)
    { question: "What is an important consideration when setting up a computer workstation?", options: ["Ergonomics", "Overclocking", "Virus scanning", "Gaming performance"], correctAnswer: 0 },
    { question: "Which device is essential for input at a workstation?", options: ["Keyboard", "Monitor", "Printer", "Speaker"], correctAnswer: 0 },
    { question: "What is an ergonomic practice to prevent repetitive strain injury?", options: ["Maintain proper posture", "Sit without breaks", "Use a heavy keyboard", "Ignore discomfort"], correctAnswer: 0 },
    { question: "What should you check for when setting up cables for a workstation?", options: ["They should not create trip hazards", "They must be tangled", "They should be visible", "They should be unplugged"], correctAnswer: 0 },
    { question: "How can you reduce glare on a monitor?", options: ["Adjust monitor position", "Increase brightness", "Wear sunglasses", "Cover the screen"], correctAnswer: 0 },
    { question: "Why is proper chair adjustment important at a workstation?", options: ["It prevents back pain", "It increases computer speed", "It improves internet connectivity", "It enhances audio quality"], correctAnswer: 0 },
    { question: "What does 'plug and play' refer to in a workstation setup?", options: ["Devices that work immediately when connected", "Devices that require complex installation", "Devices that are only for gaming", "Devices that need manual drivers"], correctAnswer: 0 },
    { question: "Which safety consideration is important when setting up a PC?", options: ["Avoiding electrical hazards", "Overloading with apps", "Using outdated software", "Skipping the manual"], correctAnswer: 0 },
    { question: "What should you do if you experience discomfort at your workstation?", options: ["Take a break and adjust your setup", "Ignore it", "Increase screen brightness", "Use more peripherals"], correctAnswer: 0 },
    { question: "What is the purpose of cable management in a workstation?", options: ["To prevent tripping hazards", "To slow down the computer", "To reduce sound", "To improve network speed"], correctAnswer: 0 },
    { question: "How can you quickly switch between open applications on a workstation?", options: ["Using ALT+TAB", "Using a touchscreen", "Clicking on the desktop", "Restarting the computer"], correctAnswer: 0 },
    { question: "Which of the following is a sign that a workstation is set up ergonomically?", options: ["Monitor at eye level", "Keyboard placed high above the desk", "Chair at a steep angle", "Mouse located far from the keyboard"], correctAnswer: 0 },
    { question: "What is the recommended approach for setting up a laptop for first-time use?", options: ["Allow the system to acclimatize and follow setup instructions", "Immediately install software", "Ignore the manual", "Use it without charging"], correctAnswer: 0 },
    { question: "What feature helps prevent muscle strain when using a mouse?", options: ["Ergonomically designed mouse", "High sensitivity settings", "Small size", "Wired connection"], correctAnswer: 0 },
    { question: "What is a common method to improve productivity when navigating the desktop?", options: ["Using keyboard shortcuts", "Using only the mouse", "Relying solely on the touchpad", "Using screen savers"], correctAnswer: 0 },

    // Module 1 / Unit 3 – Using an OS (20 questions)
    { question: "What is the primary purpose of an operating system?", options: ["To manage hardware and software resources", "To design websites", "To store large amounts of data", "To manufacture hardware components"], correctAnswer: 0 },
    { question: "Which interface allows users to interact with the operating system using icons and menus?", options: ["Graphical User Interface (GUI)", "Command Line Interface (CLI)", "Firmware Interface", "Hardware Interface"], correctAnswer: 0 },
    { question: "What function does File Explorer serve in Windows?", options: ["Navigating and managing files", "Editing documents", "Running applications", "Managing system memory"], correctAnswer: 0 },
    { question: "Which operating system is known for its WIMP interface?", options: ["Windows", "Linux", "UNIX", "DOS"], correctAnswer: 0 },
    { question: "What does UEFI stand for?", options: ["Unified Extensible Firmware Interface", "Universal Electronic Firmware Integration", "Unified Electronic Function Interface", "User-Friendly Extension Interface"], correctAnswer: 0 },
    { question: "Which operating system is an example of an open source OS?", options: ["Linux", "Windows", "macOS", "iOS"], correctAnswer: 0 },
    { question: "Which OS is designed exclusively for Apple computers?", options: ["macOS", "Windows", "Linux", "Chrome OS"], correctAnswer: 0 },
    { question: "What is the term for the default page displayed when a web browser starts?", options: ["Home page", "Bookmark", "Search engine", "History page"], correctAnswer: 0 },
    { question: "Which key combination opens a new browser tab in most browsers?", options: ["CTRL+T", "CTRL+W", "ALT+F4", "SHIFT+TAB"], correctAnswer: 0 },
    { question: "What is the purpose of a web browser?", options: ["To access and display web pages", "To manage system files", "To edit documents", "To process calculations"], correctAnswer: 0 },
    { question: "Which browser is recommended for a consistent experience across Windows devices?", options: ["Microsoft Edge", "Internet Explorer", "Mozilla Firefox", "Google Chrome"], correctAnswer: 0 },
    { question: "What does URL stand for?", options: ["Uniform Resource Locator", "Universal Resource Link", "User Reference Line", "Unified Resource Locator"], correctAnswer: 0 },
    { question: "What is the role of the Registry in Windows?", options: ["To store system configuration settings", "To manage user accounts", "To host applications", "To display web pages"], correctAnswer: 0 },
    { question: "Which tool is used to modify system settings via a command-line interface in Windows?", options: ["PowerShell", "Notepad", "File Explorer", "Task Manager"], correctAnswer: 0 },
    { question: "What function does the Control Panel serve in Windows?", options: ["Configuring system settings", "Browsing the internet", "Managing user files", "Running antivirus scans"], correctAnswer: 0 },
    { question: "Which operating system feature allows users to restore previous versions of files?", options: ["System Restore", "Task Manager", "Control Panel", "Device Manager"], correctAnswer: 0 },
    { question: "Which of the following is a benefit of using a graphical user interface?", options: ["Ease of use for non-technical users", "Higher system performance", "Reduced hardware costs", "Enhanced security"], correctAnswer: 0 },
    { question: "Which version of Windows introduced the concept of Windows as a service?", options: ["Windows 10", "Windows 8", "Windows 7", "Windows XP"], correctAnswer: 0 },
    { question: "What is the purpose of using a command prompt in an operating system?", options: ["To execute text-based commands", "To play multimedia files", "To manage network settings", "To update drivers"], correctAnswer: 0 },
    { question: "What does the term 'legacy software' refer to?", options: ["Older software that may not be compatible with new systems", "Newly released software", "Software developed for mobile devices", "Open source software"], correctAnswer: 0 },

    // Module 1 / Unit 4 – Managing an OS (20 questions)
    { question: "What is the function of Task Manager in Windows?", options: ["To monitor and manage running processes", "To install software updates", "To adjust screen brightness", "To manage network connections"], correctAnswer: 0 },
    { question: "Which tool allows users to directly edit the Windows Registry?", options: ["Registry Editor", "Control Panel", "File Explorer", "Task Manager"], correctAnswer: 0 },
    { question: "What does the principle of least privilege refer to?", options: ["Giving users only the permissions they need", "Granting all users administrative rights", "Allowing unrestricted access to files", "Disabling user accounts"], correctAnswer: 0 },
    { question: "What is the purpose of User Account Control (UAC) in Windows?", options: ["To prompt for administrator credentials for critical changes", "To speed up the system", "To manage file storage", "To disable background processes"], correctAnswer: 0 },
    { question: "Which of the following is used to schedule automated tasks in Windows?", options: ["Task Scheduler", "Disk Management", "Registry Editor", "Control Panel"], correctAnswer: 0 },
    { question: "What is virtual memory?", options: ["A portion of the hard disk used to extend RAM", "A type of physical memory", "The system's cache memory", "A component of the CPU"], correctAnswer: 0 },
    { question: "Which Windows utility is used for disk partitioning?", options: ["Disk Management", "Task Manager", "Device Manager", "File Explorer"], correctAnswer: 0 },
    { question: "What is the term used for ending a process that is not responding?", options: ["Killing a process", "Starting a process", "Hibernating a process", "Cloning a process"], correctAnswer: 0 },
    { question: "Which interface is commonly used for advanced system configuration in Windows?", options: ["Command Prompt", "File Explorer", "Notepad", "Calculator"], correctAnswer: 0 },
    { question: "What is the purpose of the Services snap-in in Windows?", options: ["To manage background services", "To create user accounts", "To edit system files", "To browse the internet"], correctAnswer: 0 },
    { question: "Which of the following best describes the function of the pagefile?", options: ["It provides virtual memory to supplement RAM", "It stores permanent data", "It manages disk partitions", "It monitors system performance"], correctAnswer: 0 },
    { question: "What is the primary role of device drivers?", options: ["To allow the OS to communicate with hardware", "To protect the system from viruses", "To provide user authentication", "To manage file storage"], correctAnswer: 0 },
    { question: "Which Windows tool provides a graphical representation of system resource usage?", options: ["Task Manager", "Registry Editor", "Control Panel", "File Explorer"], correctAnswer: 0 },
    { question: "What is the purpose of Disk Defragmenter?", options: ["To reorganize data on the hard drive for efficiency", "To increase screen resolution", "To manage user accounts", "To delete temporary files"], correctAnswer: 0 },
    { question: "What is a snap-in in the context of Windows Management Consoles?", options: ["A modular component used for managing specific system settings", "A type of file", "A network protocol", "A hardware device"], correctAnswer: 0 },
    { question: "Which command-line tool is used to terminate processes in Windows?", options: ["taskkill", "ipconfig", "netstat", "chkdsk"], correctAnswer: 0 },
    { question: "What is the role of memory management in an operating system?", options: ["To allocate and manage system memory for processes", "To manage file storage", "To control peripheral devices", "To manage user interfaces"], correctAnswer: 0 },
    { question: "Which utility would you use to view detailed system performance metrics?", options: ["Performance Monitor", "Task Scheduler", "Disk Management", "Device Manager"], correctAnswer: 0 },
    { question: "What is the purpose of the command prompt?", options: ["To execute system commands", "To display images", "To play media files", "To manage internet connections"], correctAnswer: 0 },
    { question: "Which management interface in Windows allows direct access to system settings?", options: ["Control Panel", "Microsoft Edge", "Notepad", "Windows Media Player"], correctAnswer: 0 },

    // Module 1 / Unit 5 – Troubleshooting and Support (10 questions)
    { question: "What is the first step in troubleshooting a computer problem?", options: ["Identify the problem", "Replace the hardware", "Reinstall the OS", "Ignore the issue"], correctAnswer: 0 },
    { question: "Which troubleshooting method involves gathering information and testing theories?", options: ["Divide and conquer", "Guess and check", "Random replacement", "Ignore the symptoms"], correctAnswer: 0 },
    { question: "What should be done after confirming the root cause of a computer issue?", options: ["Implement a solution", "Restart the computer", "Reboot the system", "Document the findings"], correctAnswer: 0 },
    { question: "Why is documentation important in troubleshooting?", options: ["It helps prevent future issues", "It speeds up the computer", "It reduces energy consumption", "It enhances visual display"], correctAnswer: 0 },
    { question: "Which of the following is a common tool used for troubleshooting in IT support?", options: ["Knowledge base", "Web browser", "Task Manager", "PowerShell"], correctAnswer: 0 },
    { question: "What is a key benefit of following a structured troubleshooting methodology?", options: ["Efficient problem resolution", "Increased computer speed", "Enhanced graphics performance", "Reduced file size"], correctAnswer: 0 },
    { question: "What should you do if your initial troubleshooting theory is not confirmed?", options: ["Develop a new theory", "Ignore the problem", "Reboot the system immediately", "Replace all hardware"], correctAnswer: 0 },
    { question: "In troubleshooting, what does 'escalate' mean?", options: ["To refer the issue to higher-level support", "To restart the system", "To increase system performance", "To ignore minor issues"], correctAnswer: 0 },
    { question: "Which phase of troubleshooting involves testing the proposed solution?", options: ["Implementation", "Identification", "Documentation", "Theory development"], correctAnswer: 0 },
    { question: "What is the final step in a troubleshooting process?", options: ["Verify full system functionality", "Restart the computer", "Turn off the system", "Call technical support"], correctAnswer: 0 },

    // Module 2 – Using Apps and Databases (30 questions)
    // Unit 1: Using Data Types and Units (5 questions)
    { question: "Which of the following is a common data type in programming?", options: ["Integer", "Fahrenheit", "Twilight", "Circular"], correctAnswer: 0 },
    { question: "What does a byte represent in data measurement?", options: ["A unit of digital information", "A type of hardware", "A unit of time", "A network protocol"], correctAnswer: 0 },
    { question: "What is the main purpose of data representation in computing?", options: ["To display data in various formats", "To increase file size", "To slow down processing", "To manage peripheral devices"], correctAnswer: 0 },
    { question: "Which unit is commonly used to measure digital storage?", options: ["Byte", "Meter", "Gram", "Second"], correctAnswer: 0 },
    { question: "What is a data type?", options: ["A classification that tells how data will be used", "A computer hardware component", "A type of software license", "A network protocol"], correctAnswer: 0 },
    // Unit 2: Using Apps (10 questions)
    { question: "What is application software designed to do?", options: ["Perform specific tasks for users", "Manage hardware resources", "Control the operating system", "Monitor network traffic"], correctAnswer: 0 },
    { question: "Which of the following is an example of productivity software?", options: ["Word processor", "Web browser", "Antivirus", "Operating system"], correctAnswer: 0 },
    { question: "What does 'installing an application' mean?", options: ["Setting up the software on a computer", "Deleting a program", "Upgrading hardware", "Configuring network settings"], correctAnswer: 0 },
    { question: "Which term describes software that facilitates collaboration among users?", options: ["Collaboration software", "Firmware", "Utility software", "System software"], correctAnswer: 0 },
    { question: "What is the purpose of software licensing?", options: ["To legally authorize the use of software", "To increase computer speed", "To manage data storage", "To control hardware functions"], correctAnswer: 0 },
    { question: "Which of the following is a benefit of using application software?", options: ["Increased productivity", "Higher energy consumption", "Reduced system stability", "Increased hardware complexity"], correctAnswer: 0 },
    { question: "What is the main difference between desktop and mobile applications?", options: ["Desktop apps are for stationary PCs while mobile apps are optimized for touch", "Desktop apps are always free", "Mobile apps require no installation", "Desktop apps run in web browsers"], correctAnswer: 0 },
    { question: "What does it mean to 'uninstall' an application?", options: ["Remove the software from the computer", "Install an update", "Create a backup", "Run a security scan"], correctAnswer: 0 },
    { question: "Which of the following is an example of collaboration software?", options: ["Email client", "Spreadsheet", "Web browser", "Video conferencing tool"], correctAnswer: 3 },
    { question: "What is a common feature of business software?", options: ["It improves efficiency in business processes", "It only runs on mobile devices", "It is not updated regularly", "It does not support data sharing"], correctAnswer: 0 },
    // Unit 3: Programming and App Development (10 questions)
    { question: "What is a programming language?", options: ["A set of instructions used to create software", "A type of computer hardware", "A network protocol", "A user interface"], correctAnswer: 0 },
    { question: "Which concept involves defining a blueprint for objects in object-oriented programming?", options: ["Class", "Variable", "Loop", "Array"], correctAnswer: 0 },
    { question: "What does 'debugging' refer to in programming?", options: ["Finding and fixing errors in code", "Writing code from scratch", "Designing hardware", "Formatting a hard drive"], correctAnswer: 0 },
    { question: "Which of the following is an example of a scripting language?", options: ["Python", "HTML", "CSS", "SQL"], correctAnswer: 0 },
    { question: "What is the purpose of an Integrated Development Environment (IDE)?", options: ["To provide tools for writing, testing, and debugging code", "To manage network connections", "To store user data", "To update the operating system"], correctAnswer: 0 },
    { question: "What does 'source code' refer to?", options: ["The human-readable instructions written by a programmer", "The compiled machine code", "The computer's firmware", "The user manual"], correctAnswer: 0 },
    { question: "Which of the following best describes an algorithm?", options: ["A step-by-step procedure for solving a problem", "A programming language", "A type of hardware", "A network configuration"], correctAnswer: 0 },
    { question: "What is the role of a compiler in programming?", options: ["To convert source code into machine code", "To manage system memory", "To display graphics", "To edit text files"], correctAnswer: 0 },
    { question: "What is a common use for a scripting language in web development?", options: ["Automating tasks on a webpage", "Designing hardware circuits", "Managing databases", "Creating operating systems"], correctAnswer: 0 },
    { question: "Which term describes a block of code that can be reused in programming?", options: ["Function", "Variable", "Constant", "Loop"], correctAnswer: 0 },
    // Unit 4: Using Databases (5 questions)
    { question: "What is a database?", options: ["A structured collection of data", "A type of operating system", "A computer network", "A programming language"], correctAnswer: 0 },
    { question: "What is a primary key in a relational database?", options: ["A unique identifier for a record", "A type of encryption", "A network address", "A foreign language"], correctAnswer: 0 },
    { question: "Which language is commonly used to query databases?", options: ["SQL", "HTML", "Python", "C++"], correctAnswer: 0 },
    { question: "What is the purpose of normalization in databases?", options: ["To reduce data redundancy", "To increase file size", "To slow down queries", "To enhance security"], correctAnswer: 0 },
    { question: "Which type of database model organizes data into tables?", options: ["Relational", "Hierarchical", "Network", "Object-oriented"], correctAnswer: 0 },

    // Module 3 – Using Computer Hardware (30 questions)
    // Unit 1: System Components (10 questions, Q116–Q125)
    { question: "What is the motherboard?", options: ["The main circuit board that connects all components", "A type of memory", "A peripheral device", "A software application"], correctAnswer: 0 },
    { question: "Which component is responsible for executing instructions in a computer?", options: ["CPU", "GPU", "RAM", "Motherboard"], correctAnswer: 0 },
    { question: "What does PSU stand for?", options: ["Power Supply Unit", "Primary System Unit", "Processing Speed Unit", "Peripheral Support Unit"], correctAnswer: 0 },
    { question: "Which component is used to temporarily store data for quick access?", options: ["RAM", "Hard Disk", "SSD", "Motherboard"], correctAnswer: 0 },
    { question: "What is the role of the BIOS?", options: ["To initialize hardware during boot", "To store user data", "To process calculations", "To connect to the internet"], correctAnswer: 0 },
    { question: "Which of the following is a type of expansion slot on a motherboard?", options: ["PCI Express", "USB", "HDMI", "Ethernet"], correctAnswer: 0 },
    { question: "What is the function of a chipset on a motherboard?", options: ["To manage data flow between the CPU, memory, and peripherals", "To increase screen resolution", "To store data permanently", "To cool the CPU"], correctAnswer: 0 },
    { question: "Which component can be upgraded to improve a computer's performance?", options: ["RAM", "Motherboard", "CPU", "All of the above"], correctAnswer: 3 },
    { question: "What is the primary purpose of a cooling system in a computer?", options: ["To dissipate heat generated by components", "To increase network speed", "To improve audio quality", "To enhance display brightness"], correctAnswer: 0 },
    { question: "What is the purpose of CPU cache in a computer system?", options: ["To store frequently accessed data for faster processing", "To permanently store data", "To cool the processor", "To manage power supply"], correctAnswer: 0 },
    // Unit 2: Using Device Interfaces (5 questions, Q126–Q130)
    { question: "What does USB stand for?", options: ["Universal Serial Bus", "Ultra Speed Bus", "Universal System Bus", "Unique Serial Bridge"], correctAnswer: 0 },
    { question: "Which port is commonly used to connect a monitor to a computer?", options: ["HDMI", "USB", "Ethernet", "Audio Jack"], correctAnswer: 0 },
    { question: "What is the function of a network interface card (NIC)?", options: ["To enable network connectivity", "To store data", "To process instructions", "To manage power"], correctAnswer: 0 },
    { question: "Which type of connector is typically used for audio output?", options: ["3.5mm jack", "USB-C", "VGA", "Ethernet"], correctAnswer: 0 },
    { question: "What is the purpose of Bluetooth connectivity?", options: ["To allow wireless communication between devices", "To connect to the internet", "To increase storage capacity", "To enhance graphics performance"], correctAnswer: 0 },
    // Unit 3: Using Peripheral Devices (5 questions, Q131–Q135)
    { question: "Which peripheral device is primarily used for data input?", options: ["Keyboard", "Monitor", "Printer", "Speaker"], correctAnswer: 0 },
    { question: "What type of device is a scanner?", options: ["Input device", "Output device", "Storage device", "Processing device"], correctAnswer: 0 },
    { question: "Which peripheral is used to produce a hard copy of digital documents?", options: ["Printer", "Mouse", "Monitor", "Keyboard"], correctAnswer: 0 },
    { question: "What is the purpose of a webcam?", options: ["To capture video and images", "To store data", "To input text", "To display output"], correctAnswer: 0 },
    { question: "Which device converts digital signals to analog signals for audio output?", options: ["Sound card", "Graphics card", "Network card", "Motherboard"], correctAnswer: 0 },
    // Unit 4: Using Storage Devices (5 questions, Q136–Q140)
    { question: "What is the main difference between an HDD and an SSD?", options: ["SSDs have faster read/write speeds", "HDDs are more durable", "SSDs use magnetic storage", "HDDs are more expensive"], correctAnswer: 0 },
    { question: "What does 'USB flash drive' refer to?", options: ["A portable storage device", "A type of processor", "A software application", "A network cable"], correctAnswer: 0 },
    { question: "Which storage device is typically used for long-term data retention?", options: ["Hard Disk Drive", "RAM", "Cache", "CPU"], correctAnswer: 0 },
    { question: "What is an optical drive used for?", options: ["Reading and writing data to CDs/DVDs", "Storing data permanently", "Processing data", "Connecting to the internet"], correctAnswer: 0 },
    { question: "Which storage technology is known for its durability and speed?", options: ["Solid-State Drive", "Hard Disk Drive", "Floppy Disk", "CD-ROM"], correctAnswer: 0 },
    // Unit 5: Using File Systems (5 questions, Q141–Q145)
    { question: "What is a file system?", options: ["A method of organizing and storing files on a storage device", "A type of software application", "A network protocol", "A hardware component"], correctAnswer: 0 },
    { question: "What is the purpose of directories in a file system?", options: ["To organize files into a hierarchical structure", "To increase storage capacity", "To run applications", "To secure data"], correctAnswer: 0 },
    { question: "Which file attribute might indicate that a file is read-only?", options: ["A file permission setting", "File size", "File location", "File type"], correctAnswer: 0 },
    { question: "What is the function of the File Explorer?", options: ["To navigate, manage, and organize files and folders", "To process data", "To run antivirus scans", "To update the operating system"], correctAnswer: 0 },
    { question: "Which file system is commonly used by Windows operating systems?", options: ["NTFS", "FAT32", "exFAT", "EXT4"], correctAnswer: 0 },

    // Module 4 – Using Networks (30 questions)
    // Unit 1: Networking Concepts (10 questions, Q146–Q155)
    { question: "What does TCP/IP stand for?", options: ["Transmission Control Protocol/Internet Protocol", "Transfer Control Protocol/Internet Protocol", "Transmission Communication Protocol/Interconnected Protocol", "Technical Control Protocol/Internet Process"], correctAnswer: 0 },
    { question: "Which device is used to forward packets in a network?", options: ["Router", "Switch", "Hub", "Modem"], correctAnswer: 0 },
    { question: "What is the primary purpose of a firewall?", options: ["To block unauthorized network access", "To store data", "To increase computer speed", "To manage user accounts"], correctAnswer: 0 },
    { question: "What does DNS stand for?", options: ["Domain Name System", "Digital Network Service", "Data Number System", "Domain Navigation Software"], correctAnswer: 0 },
    { question: "Which device is used to connect multiple computers in a network?", options: ["Switch", "Printer", "Monitor", "Keyboard"], correctAnswer: 0 },
    { question: "What is an IP address?", options: ["A unique identifier for a device on a network", "A type of storage", "A computer virus", "An operating system"], correctAnswer: 0 },
    { question: "Which protocol is used for secure communication over a network?", options: ["HTTPS", "HTTP", "FTP", "SMTP"], correctAnswer: 0 },
    { question: "What does LAN stand for?", options: ["Local Area Network", "Large Area Network", "Long Area Network", "Lightweight Area Network"], correctAnswer: 0 },
    { question: "What does WAN stand for?", options: ["Wide Area Network", "Wireless Area Network", "Web Area Network", "Wide Application Network"], correctAnswer: 0 },
    { question: "What is a network topology?", options: ["The arrangement of network devices and cables", "A type of computer virus", "A programming language", "A storage method"], correctAnswer: 0 },
    // Unit 2: Connecting to a Network (5 questions, Q156–Q160)
    { question: "Which connection type is typically used for home broadband?", options: ["Ethernet", "Parallel", "Serial", "SCSI"], correctAnswer: 0 },
    { question: "What is the purpose of a wireless router?", options: ["To provide Wi-Fi connectivity", "To increase storage capacity", "To process data", "To manage user accounts"], correctAnswer: 0 },
    { question: "Which wireless standard is commonly used in home networks?", options: ["802.11n", "802.3", "802.15", "802.16"], correctAnswer: 0 },
    { question: "What does VPN stand for?", options: ["Virtual Private Network", "Visible Public Network", "Virtual Public Node", "Verified Private Network"], correctAnswer: 0 },
    { question: "Which device can act as a modem for internet connectivity?", options: ["Cable modem", "Printer", "Monitor", "Keyboard"], correctAnswer: 0 },
    // Unit 3: Secure Web Browsing (5 questions, Q161–Q165)
    { question: "What is phishing?", options: ["A fraudulent attempt to obtain sensitive information", "A method of data encryption", "A type of computer virus", "A network configuration"], correctAnswer: 0 },
    { question: "What is one way to secure web browsing?", options: ["Using HTTPS", "Disabling the firewall", "Ignoring software updates", "Using weak passwords"], correctAnswer: 0 },
    { question: "What is the role of digital certificates in web security?", options: ["To authenticate websites", "To slow down the connection", "To manage files", "To control hardware"], correctAnswer: 0 },
    { question: "What should you do if you receive a suspicious email with a link?", options: ["Do not click the link and verify the sender", "Immediately click the link", "Forward the email without checking", "Reply with personal information"], correctAnswer: 0 },
    { question: "Which browser feature helps protect against malicious websites?", options: ["Built-in security warnings", "Increased screen brightness", "Automatic file deletion", "Faster loading times"], correctAnswer: 0 },
    // Unit 4: Using Shared Storage (5 questions, Q166–Q170)
    { question: "What is file sharing in a network?", options: ["Allowing multiple users to access files on a server", "A method of data encryption", "A type of computer virus", "A method of hardware installation"], correctAnswer: 0 },
    { question: "Which protocol is commonly used for file sharing in Windows?", options: ["SMB", "FTP", "HTTP", "SMTP"], correctAnswer: 0 },
    { question: "What is the purpose of network attached storage (NAS)?", options: ["To provide centralized file storage", "To speed up the computer", "To process data", "To manage user accounts"], correctAnswer: 0 },
    { question: "Which feature is important for data backup in shared storage?", options: ["Regular backups", "Increased CPU speed", "Overclocking", "Disabling security"], correctAnswer: 0 },
    { question: "What does RAID stand for in storage systems?", options: ["Redundant Array of Independent Disks", "Random Access of Indexed Data", "Readily Available Information Device", "Reliable Array of Internal Data"], correctAnswer: 0 },
    // Unit 5: Using Mobile Devices (5 questions, Q171–Q175)
    { question: "What is a key characteristic of mobile devices?", options: ["Portability", "High power consumption", "Fixed location", "Large size"], correctAnswer: 0 },
    { question: "Which operating system is commonly used in smartphones?", options: ["Android", "Windows XP", "macOS", "Linux (desktop)"], correctAnswer: 0 },
    { question: "What is the purpose of mobile apps?", options: ["To provide functionality specific to mobile devices", "To manage desktop settings", "To run server applications", "To edit hardware components"], correctAnswer: 0 },
    { question: "What is the significance of app stores in mobile devices?", options: ["They provide a centralized location to download apps", "They increase device weight", "They reduce battery life", "They are used for file sharing"], correctAnswer: 0 },
    { question: "Which connectivity option is commonly used by mobile devices?", options: ["Wi-Fi", "Ethernet", "SCSI", "Parallel port"], correctAnswer: 0 },

    // Module 5 – Security Concepts (25 questions, Q176–Q200)
    // Unit 1: Security Concerns (7 questions, Q176–Q182)
    { question: "What is malware?", options: ["Software designed to harm a computer system", "A type of operating system", "A network device", "A hardware component"], correctAnswer: 0 },
    { question: "What does antivirus software do?", options: ["Detects and removes malicious software", "Increases CPU speed", "Formats the hard drive", "Manages user accounts"], correctAnswer: 0 },
    { question: "What is social engineering in the context of IT security?", options: ["Manipulating individuals to divulge confidential information", "Designing secure networks", "Creating hardware firewalls", "Encrypting data"], correctAnswer: 0 },
    { question: "What is the purpose of a firewall in cybersecurity?", options: ["To block unauthorized access to a network", "To increase network speed", "To store data", "To enhance graphics performance"], correctAnswer: 0 },
    { question: "Which of the following is an example of a physical security measure?", options: ["Locked server room", "Antivirus software", "Firewall", "Encryption"], correctAnswer: 0 },
    { question: "What is the concept of 'defense in depth'?", options: ["Using multiple layers of security controls", "Relying on a single security measure", "Disabling all security features", "Focusing only on physical security"], correctAnswer: 0 },
    { question: "What is a common risk associated with weak passwords?", options: ["Unauthorized access", "Faster system performance", "Increased storage capacity", "Better compatibility"], correctAnswer: 0 },
    // Unit 2: Using Best Practices (7 questions, Q183–Q189)
    { question: "Why is it important to keep software up-to-date?", options: ["To patch security vulnerabilities", "To increase system overheating", "To slow down performance", "To disable antivirus software"], correctAnswer: 0 },
    { question: "What is the role of patch management?", options: ["To update software with fixes and improvements", "To create new hardware", "To delete files", "To manage user accounts"], correctAnswer: 0 },
    { question: "Which practice helps protect against malware?", options: ["Using reputable software sources", "Downloading from unknown websites", "Ignoring software updates", "Sharing passwords"], correctAnswer: 0 },
    { question: "What is the benefit of implementing strong password policies?", options: ["Improved account security", "Faster internet speed", "Enhanced graphics", "Increased file size"], correctAnswer: 0 },
    { question: "Why should you avoid using default passwords?", options: ["They are widely known and can be exploited", "They are too complex", "They enhance security", "They improve system performance"], correctAnswer: 0 },
    { question: "What is multi-factor authentication?", options: ["Using multiple methods to verify identity", "Using a single password", "Using only a PIN", "Using a fingerprint alone"], correctAnswer: 0 },
    { question: "Which of the following is a best practice for email security?", options: ["Not clicking on suspicious links", "Sharing personal information", "Using weak passwords", "Ignoring security warnings"], correctAnswer: 0 },
    // Unit 3: Using Access Controls (5 questions, Q190–Q194)
    { question: "What is the purpose of access control in security?", options: ["To restrict access to authorized users", "To increase system speed", "To store large amounts of data", "To disable antivirus software"], correctAnswer: 0 },
    { question: "What is authentication?", options: ["The process of verifying a user's identity", "A type of malware", "A network protocol", "A storage method"], correctAnswer: 0 },
    { question: "Which factor is NOT typically used in multi-factor authentication?", options: ["User's favorite color", "Something you know", "Something you have", "Something you are"], correctAnswer: 0 },
    { question: "What is encryption?", options: ["The process of converting information into a secure format", "A method of increasing system speed", "A type of hardware", "A network protocol"], correctAnswer: 0 },
    { question: "What is the role of password management tools?", options: ["To securely store and manage passwords", "To increase screen resolution", "To monitor network traffic", "To defragment the hard drive"], correctAnswer: 0 },
    // Unit 4: Behavioral Security Concepts (5 questions, Q195–Q199)
    { question: "What are acceptable use policies?", options: ["Rules that define how company resources can be used", "Guidelines for network speed", "Instructions for software installation", "Procedures for hardware repair"], correctAnswer: 0 },
    { question: "Why is employee training important in security?", options: ["To prevent social engineering attacks", "To slow down the computer", "To increase file size", "To disable antivirus software"], correctAnswer: 0 },
    { question: "What does the term 'privacy expectations' refer to?", options: ["The assumption that personal data will be protected", "The speed of data processing", "The layout of a network", "The performance of an application"], correctAnswer: 0 },
    { question: "What is the purpose of incident response planning?", options: ["To prepare for and manage security breaches", "To increase internet speed", "To upgrade hardware", "To disable firewalls"], correctAnswer: 0 },
    { question: "What does the term 'data breach' refer to?", options: ["Unauthorized access to confidential information", "A routine software update", "A type of computer virus", "A hardware malfunction"], correctAnswer: 0 },
    // Extra question for Module 5
    { question: "What is phishing, and why is it dangerous?", options: ["It is a cyber attack aimed at tricking users into revealing sensitive information", "It is a method of data backup", "It is a type of hardware upgrade", "It is a network optimization technique"], correctAnswer: 0 }
];

        let currentQuestion = localStorage.getItem('currentQuestion') ? parseInt(localStorage.getItem('currentQuestion')) : 0;
        let score = localStorage.getItem('score') ? parseInt(localStorage.getItem('score')) : 0;
        let userAnswers = JSON.parse(localStorage.getItem('userAnswers')) || [];

        function loadQuestion() {
            document.getElementById('progress').innerText = `Question ${currentQuestion + 1} of ${questions.length}`;
            document.getElementById('question').innerText = questions[currentQuestion].question;
            const optionsSelect = document.getElementById('options');
            optionsSelect.innerHTML = "";
            questions[currentQuestion].options.forEach((option, index) => {
                const opt = document.createElement('option');
                opt.value = index;
                opt.innerText = option;
                optionsSelect.appendChild(opt);
            });
        }

        function submitAnswer() {
            const selectedOption = document.getElementById('options').value;
            const resultDiv = document.getElementById('result');
            userAnswers[currentQuestion] = selectedOption;
            if (selectedOption == questions[currentQuestion].correctAnswer) {
                score++;
                resultDiv.innerText = "Correct!";
                resultDiv.style.color = "green";
            } else {
                resultDiv.innerText = `Incorrect. Correct answer: ${questions[currentQuestion].options[questions[currentQuestion].correctAnswer]}`;
                resultDiv.style.color = "red";
            }
            
            localStorage.setItem('score', score);
            localStorage.setItem('userAnswers', JSON.stringify(userAnswers));
            currentQuestion++;
            localStorage.setItem('currentQuestion', currentQuestion);

            setTimeout(() => {
                resultDiv.innerText = "";
                if (currentQuestion < questions.length) {
                    loadQuestion();
                } else {
                    document.querySelector('.card').style.display = 'none';
                    let percentage = ((score / questions.length) * 100).toFixed(2);
                    document.getElementById('score').innerText = `You scored ${score} out of ${questions.length} (${percentage}%)`;
                    document.getElementById('score').style.display = 'block';
                    showReview();
                    localStorage.clear();
                }
            }, 2000);
        }

        function showReview() {
            document.getElementById('reviewSection').style.display = 'block';
            const reviewContent = document.getElementById('reviewContent');
            reviewContent.innerHTML = "";
            questions.forEach((q, index) => {
                const div = document.createElement('div');
                div.innerHTML = `<strong>Q${index + 1}: ${q.question}</strong><br> Your Answer: ${q.options[userAnswers[index]] || "Not answered"} <br> Correct Answer: ${q.options[q.correctAnswer]}<br><br>`;
                reviewContent.appendChild(div);
            });
        }

        loadQuestion();
    </script>
</body>
</html>

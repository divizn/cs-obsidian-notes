- Also known as system utilities
- Provide convenient environment for program development and execution
- Some of them are simply user interfaces to syscalls (e.g. run on Windows makes syscalls to the windows API to initiate the execution of a program)
- Others are more complex, e.g. device drivers

# System Program Categories

### File management

- These programs create, delete, copy, rename, print, dump, list, and generally manipulate files and directories (e.g. dolphin file manager or windows explorer)

### Status Information

- Some programs simply ask the system for the date, time, amount of available memory, or disk space, number of users, or similar status information.
- Others are more complex, providing detailed performance, logging and debugging information
- Example - task manager

### File modification

- Text editors and file content search/text transformations, etc. (Obsidian, Visual Studio, VSCode, IntelliJ, or anything that modifies files really tbh)

### Programming-language support

- Compilers, assemblers, debuggers, and interpreters for common programming languages (such as C, C++, Java, and PERL)

### Program loading and execution

- Once a program is assembled or compiled, it must be loaded into memory to be executed
- Loaders, linkers, debuggers, etc.

### Communications

- These programs provide the mechanism for creating virtual connections among processes, users, and computer systems.
- Allow users to send messages to one another's screens, to browse web pages, to send e-mail messages, to log in remotely, or to transfer files from one machine to another

### Background services

- All general-purpose systems have methods for launching certain system-program processes at boot time
- Some of these processes terminate after completing their tasks, while others continue to run until the system halts.
- Constantly running system-program processes are known as **services, subsystems, or daemons**.
- Includes schedulers, system monitors, printer servers, etc.
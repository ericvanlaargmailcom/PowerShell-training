# PowerShell pipeline basics

Note: as with most PowerShell exercises, it's best not to copy-paste the command's, but to actually type them. Use keyboard navigation (arrow up/down, home, end) to speed up entering commands in PowerShell.

## Task 1: Measuring
1. Open a PowerShell console.
1. Run this command: ```Get-Command```
1. This will display a listing of all commands in PowerShell.
1. Run this command: ```Get-Command | Measure-Object```
1. This command measures the number of command's in PowerShell. Notice the total number of commands.
1. Run this command: ```Get-Command -verb stop```
1. This will display a listing of all commands in PowerShell that have a verb of **stop**.
1. Run this command: ```Get-Command -verb stop | Measure-Object```
1. This command measures the number of command's in PowerShell that have a verb of **stop**. Notice the total number of commands.
1. Run this command: ```Get-Process```
1. This will display a process listing.
1. Run this command: ```Get-Process | Measure-Object```
1. This command measures the number of processes.
1. Run this command: ```Get-Process w*```
1. This command displays a list of processes with a name that starts with **w**. Count the number of processes.
1. Run this command: ```Get-Process w* | Measure-Object```
1. This command measures the number of processes with a name that starts with **w**. Verify that the number is correct.


## Task 2: Sorting
1. Open a PowerShell console.
1. Run this command: ```Get-Process```
1. This will display a process listing. Notice it is sorted alphabetically on ProcessName.
1. Run this command: ```Get-Process | Sort-Object Handles```
1. Notice that the process listing is sorted on the Handles column.
1. Run this command: ```Get-Process | Sort-Object Handles -Descending```
1. Notice that the process listing is sorted descending  on the Handles column.
1. Run this command: ```Get-Process | Sort id```
1. The result is sorted on the id column. Please notice the use of the sort alias instead of the Sort-Object cmdlet. Many commands that have a **Object** Noun, an alias exists without the noun. For example, Sort is an alias for Sort-Object, Measure is an alias for Measure-Object.


## Task 3: Grouping
1. Run this command: ```Get-Command```
1. This will display a listing of all commands in PowerShell. Notice the header of the table: all command's have a specific **CommandType**.
1. Run this command: ```Get-Command | Group-Object CommandType```
1. This will group all commands by CommandType. Notice that most commands are either a Function or a Cmdlet.
1. Retrieve a service listing by running this command: ```Get-Service```
1. Notice that all services have a status. Most are running or stopped.
1. Run this command: ```Get-Service | Group-Object Status```
1. This will group all services by Status. Notice that most services are either running or stopped.
1. The Count column specifies the number of services with a specific status. The Name column does not refer to the service name, but to the name of the status. Most will be Stopped or Started. The Group column contains all services with a specific status. The curly brackets { } indicate it's a collection of objects.

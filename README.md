# File_Allocation_Table_FIN
This is a File Allocation Table - FAT implementation in Python.
The code implements a simple file system simulation using a FAT (File Allocation Table) data structure. 
The file system is stored in a virtual hard disk drive (HDD) represented by a 2D matrix. 
The code provides various functions to interact with the file system, such as creating files, deleting files, reading files, 
renaming files, and displaying file system information.

Constants:
UA_Size: Size of each allocation unit (UA) in bytes.
NR_UA: Total number of allocation units in the virtual HDD.
NR_UA_FAT: Number of allocation units used for the FAT.
NR_UA_ROOT: Number of allocation units used for the root directory.
NAME: Length of the file name in the root directory.
EXT: Length of the file extension in the root directory.
DIM: Length of the file size and starting UA in the root directory.
START_UA: Starting allocation unit index in the root directory.
FLAG: Flag value in the root directory.


Data Structures:
HDD: Represents the virtual hard disk drive. It is a 2D matrix with NR_UA rows and UA_Size columns.
FAT: The File Allocation Table. It is a 1D list with NR_UA elements, representing the allocation status of each allocation unit.
The values can be 0 (free), 1 (FAT), 2 (root directory), 3 (data)
ROOT: The root directory. It is a 2D matrix with NR_UA_ROOT rows and UA_Size columns. 
Each row represents a file entry, storing the file name, extension, size, starting UA, and flag.

Functions:
FAT Operations:
freeUA(): Returns the index of the first free allocation unit in the FAT or -1 if none is available.
initFat(matrix): Initializes the FAT with appropriate values for the FAT and root directory allocation units.
printFat(matrix): Prints the contents of the FAT.
updateFat(change_ua, value): Updates the allocation status of an allocation unit in the FAT.
fatOnHDD(): Updates the HDD with the contents of the FAT.
countFreeMemory(): Returns the number of free allocation units in the FAT.
Root Directory Operations:
printRoot(): Prints the contents of the root directory.
freeOnRoot(): Returns the index of the first free entry in the root directory or -1 if none is available.
insertInRoot(name, ext, size, startUA, flag): Inserts a new file entry into the root directory.
rootOnHDD(): Updates the HDD with the contents of the root directory.

HDD Operations:
printHDD(): Prints the contents of the HDD.
uploadOnHDD(data): Uploads data to the HDD by storing it in consecutive free allocation units.

Data Manipulation:
Various utility functions for converting data between different formats (bytes, integers, strings) and slicing lists into byte-sized elements.

User Functions:
processUserInput(): Takes user commands as input and performs the corresponding file system operations. Supported commands include create, read, rename, delete, ls, exit, mem stat, help, and commands. It also provides a help message for each command.

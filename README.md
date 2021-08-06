# library-management-tool
A management tool for file libraries, which can perform various user-specified functionality.  
Written by Eau Claire Energy Cooperative IT Intern Spencer Keith.  
Developed with Java 16.

## Background
Eau Claire Energy Cooperative migrated its employee files from a local network drive to Microsoft OneDrive. During the process, IT Intern Spencer Keith thought it potentially helpful to write a program that could assist with this process by performing analysis on company files, to distinguish which files should be migrated, and which could be left behind.

## Install
To install, simply clone the repository or download the source code .zip file.

## Dependencies
This program uses the Apache POI API. To use this API, add the following to your pom.xml file:  

```xml
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi</artifactId>
    <version>5.0.0</version>
</dependency>
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi-ooxml</artifactId>
    <version>5.0.0</version>
</dependency>
```

## Usage
As of August 3, 2021, the program can perform 5 different functions:
1. Generate an empty, identical duplicate file structure of a file structure at a specified location for archiving.
2. Populate a generated archive with files last modified before a given date.
3. Generate an informational Excel Workbook with three sheets. The first lists all files in a given location with their filepath, size, and last modified date. The final of these is conditionally highlighted according to given threshold dates. The second lists all files last modifed before a given date ("old" files). The third lists all files with identical duplicates in the specified location.
4. Delete empty directories within a specified location.
5. Delete all instances of a given file, by name.

To run a function, execute the program (main method in "client" class) with command line arguments.
1. "Gen_Arch"/"1"   [filepath of source location]   [filepath of archive destination]
2. "Arch_Files"/"2"   [filepath of source location]   [filepath of archive destination]   [last modified date threshold]
3. "Gen_SS"/"3"   [filepath of source location]   [filepath of output spreadsheet]   [number of threads to use]   ["old" date threshold]   *OPTIONAL*[red-highlighted "oldest" date threshold]   *OPTIONAL*[orange-highlighted "second-oldest" date threshold]   *OPTIONAL*[yellow-highlighted "newest-oldest" date threshold]
4. "Del_Empt_Dirs"/"4"   [filepath of source location]
5. "Del_File_By_Name"/"5"   [filepath of source location]   [name of file to delete]

## Syntax

Dates are given in the following format:  
YYYY-MM-DD  

*\*NOTE\** When attempting to delete empty directories using the program's fourth functionality, be weary of hidden files generated by the system.
For example, on Windows, consider running "Del_File_By_Name" for file "Thumbs.db" FIRST, then running Del_Empt_Dirs.
"Thumbs.db" files are automatically generated by Windows, and can be found in numerous locations.

Filepaths are given in the format of the following examples:  
C:\Users\skeith\Desktop\ARCHIVE_FOLDER  
C:\Users\skeith\Desktop\File_Library_Spreadsheet.xlsx

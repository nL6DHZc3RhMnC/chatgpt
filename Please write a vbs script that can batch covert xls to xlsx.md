Please write a vbs script that can batch covert xls to xlsx.

Sure, here's a VBScript that can batch convert XLS files to XLSX:

```vbnet
Option Explicit

Dim objFSO, objFolder, objFiles, objExcel, objWorkbook
Dim strFolderPath, strExtension, strNewExtension, strFile, strNewFile

' set the folder path containing the XLS files
strFolderPath = "C:\Users\Username\Desktop\XLS_Files"

' set the file extension to look for
strExtension = ".xls"

' set the new file extension
strNewExtension = ".xlsx"

' create file system object
Set objFSO = CreateObject("Scripting.FileSystemObject")

' get the folder object
Set objFolder = objFSO.GetFolder(strFolderPath)

' loop through all files in the folder
For Each objFiles In objFolder.Files

    ' check if file extension matches
    If Right(objFiles.Name, Len(strExtension)) = strExtension Then
    
        ' create new file name with new extension
        strFile = objFiles.Path
        strNewFile = Left(strFile, Len(strFile) - Len(strExtension)) & strNewExtension
        
        ' create Excel object
        Set objExcel = CreateObject("Excel.Application")
        
        ' open workbook
        Set objWorkbook = objExcel.Workbooks.Open(strFile)
        
        ' save as XLSX file
        objWorkbook.SaveAs strNewFile, 51
        
        ' close workbook and Excel object
        objWorkbook.Close False
        objExcel.Quit
        
        ' release Excel objects
        Set objWorkbook = Nothing
        Set objExcel = Nothing
    
    End If
    
Next

' release file system objects
Set objFiles = Nothing
Set objFolder = Nothing
Set objFSO = Nothing

WScript.Echo "All XLS files converted to XLSX."

```
To use this script, simply copy and paste it into a text editor (such as Notepad), save it with a .vbs extension, and run it. Make sure to update the strFolderPath variable to the folder path where your XLS files are located. The script will then loop through all XLS files in the folder, convert them to XLSX, and save them with the same file name but with the new extension.




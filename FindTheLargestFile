import glob
import os
import win32api

#Getting drive names

drives = win32api.GetLogicalDriveStrings()
drives = drives.split('\000')[:-1]
print(drives)

# largestFileSize = 0
# largestFilePath = ""
# index = 0

# Cleaning the Text File before every new search
tempSize = 0
with open('FileSizes.txt', 'w') as file:
        file.close()

# Looping through all the drives
for drive in drives:
        print("looking into drive: ", drive)
        largestFileSize = 0
        largestFilePath = ""
        allFiles = glob.glob(drive + '**\\*', recursive = True)
        for eachFile in allFiles:
                try:
                        if not os.path.isdir(eachFile):
                                tempSize = os.path.getsize(eachFile)
                        if tempSize > largestFileSize:
                                largestFileSize = tempSize
                                largestFilePath = eachFile
                except:
                        pass

# Writing the path and file size into a text file in the current working directory
        with open('FileSizes.txt', 'a') as file:
                megaBytesLargestFileSize = str(largestFileSize/1000000)
                gigaBytesLargestFileSize = str(largestFileSize/1000000000)
                file.write("__________IN " + drive
                        + ' DRIVE________________________________'
                          '__________________________________'
                          '______________________________'
                        '\n\n' + largestFilePath + '\n' + "File Size: "
                           + megaBytesLargestFileSize+ " Megabytes\n" + "\t"*1 + r"   "
                           + gigaBytesLargestFileSize + "Gigabytes\n\n")

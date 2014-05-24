---
layout: post
title: "Using Python to Backup"
description: "according to chapter Problem Solving of the book A Byte of Python, the author suggest that zipfile module could be used to create a program that backups files"
category: Coding
tags: [Python, backup, zipfile]
---
{% include JB/setup %}

I'm recently reading [*A Byte of Python*](http://www.swaroopch.com/notes/python/) by Swaroop C H (fantastic book for Python beginners BTW). The chapter [*Problem Solving*](http://www.swaroopch.com/notes/python/#problem_solving) is about creating a program that backups files. The author uses `os.system` to create the archives for pedagogical purposes and suggests the readers to try using `zipfile` or `tarfile` which are built-in modules to refine the program. 

Here is what I did: 
##Ver1
The first version is based on the original basic version mentioned in the book. It creates a zip file named by the current time and add all the files under a certain directory to it:

~~~ python
import zipfile, os, time

source = ['/Users/jared/Documents/test']
target_dir = '/Users/jared/Documents/backup_test'
backp_file_name = time.strftime('%Y%m%d%H%M%S') + '.zip'

#create a zip file
z = zipfile.ZipFile(target_dir + os.sep + backp_file_name, 'w')
#add the files to the archive
for directions in source:#for multiple sources
    for files in os.listdir(directions):
        z.write(directions + os.sep + files, files)#exclude the original directories
z.close()

#check if the backup succeed by matching the file names
lst = []
for directions in source:
    lst.append(os.listdir(directions))
if lst == [z.namelist()]:#check if all the files are zipped
    print("Congratulations, the backup succeeded.")
else:
    print("Sorry, the backup failed.")
~~~

##Ver2
A subdirectory is created in the version to store the archives categorized by date:

~~~ python
import zipfile, os, time

source = ['/Users/jared/Documents/test']
target_dir = '/Users/jared/Documents/backup_test'

subdirectory = target_dir + os.sep + time.strftime('%Y%m%d')
backp_file_name = time.strftime('%H%M%S') + '.zip'

#create the subdirectory if it does not exist
if not os.path.exists(subdirectory):
    os.mkdir(subdirectory)
    print("Successfully created directory", subdirectory)

#create a zip file
z = zipfile.ZipFile(subdirectory + os.sep + backp_file_name, 'w')
#add the files to the archive
for directions in source:
    for files in os.listdir(directions):
        z.write(directions + os.sep + files, files)#exclude the original directories
z.close()

#check if the backup succeed by matching the file names
lst = []
for directions in source:
    lst.append(os.listdir(directions))
if lst == [z.namelist()]:#check if all the files are zipped
    print("Congratulations, the backup succeeded.")
else:
    print("Sorry, the backup failed.")
~~~

##Ver3
A user-input comment is attached to the file name in this version in order to differenciate the backup files. It's like the GitHub commit :). 

~~~ python
import zipfile, os, time

source = ['/Users/jared/Documents/test']
target_dir = '/Users/jared/Documents/backup_test'

subdirectory = target_dir + os.sep + time.strftime('%Y%m%d')

#ask to enter a comment and add the comment to the backup file name
comment = input("Please enter a comment:")
if comment == 0:
    backp_file_name = time.strftime('%H%M%S') + '.zip'
else:
    backp_file_name = time.strftime('%H%M%S') + '_' + comment.replace(' ', '_') + '.zip'

if not os.path.exists(subdirectory):
    os.mkdir(subdirectory)
    print("Successfully created directory", subdirectory)

z = zipfile.ZipFile(subdirectory + os.sep + backp_file_name, 'w')
for directions in source:
    for files in os.listdir(directions):
        z.write(directions + os.sep + files, files)
z.close()

lst = []
for directions in source:
    lst.append(os.listdir(directions))
if lst == [z.namelist()]:
    print("Congratulations, the backup succeeded.")
else:
    print("Sorry, the backup failed.")
~~~
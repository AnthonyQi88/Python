# Python Memo





## Help with Jupyter Notebooks

------

We've aimed to make our Jupyter notebooks easy to use. But, if you get stuck, you can find more information [here](https://learner.coursera.help/hc/en-us/articles/360004995312-Solve-problems-with-Jupyter-Notebooks).

If you still need help, the discussion forums are a great place to find it! Use the forums to ask questions and source answers from your fellow learners.

If you want to learn more about Jupyter Notebooks as a technology, check out these resources:

- [Jupyter Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook), by datacamp.com
- [How to use Jupyter Notebooks](https://www.codecademy.com/articles/how-to-use-jupyter-notebooks), by codeacademy.com
- [Teaching and Learning with Jupyter](https://jupyter4edu.github.io/jupyter-edu-book/), by university professors using Jupyter



## Using Python to Interact with the Operating System



### Managing Files with Python

#### Reading Files

```python
[admin@c-8-client SelfLearning]$ cat haiku.txt
advance your career,
automatting with Python,
it's so fun to learn.

[admin@c-8-client SelfLearning]$ python3.8
>>> file = open("haiku.txt")
>>> print(file.readline())
advance your career,

>>> print(file.readline().strip())
automatting with Python,

>>> file = open("haiku.txt")
>>> print(file.read().strip())
advance your career,
automatting with Python,
it's so fun to learn.
>>> file.close()
```

```python
>>> with open("haiku.txt") as file:
...     print(file.readline().strip())
...
advance your career,
```

* file.readlines()

```python
>>> file = open("haiku.txt")
>>> lines = file.readlines()
>>> file.close()
>>> lines.sort()
>>> print(lines)
['advance your career,\n', 'automatting with Python,\n', "it's so fun to learn.\n"]
```

#### Writing Files

* **"r": read-only**

* **"w": write-only**

* **"a": append**

* **"r+": read-write**

  ```python
  >>> with open("New_file.txt", "w") as file:
  ...     file.write("This is the first line")
  ...
  22
  >>> file = open("New_file.txt")
  >>> print(file.read())
  This is the first line
  ```

  ```python
  >>> with open("New_file.txt", "w") as file:
  ...     file.write("This is the first line")
  ...
  22
  >>> file = open("New_file.txt")
  >>> print(file.read())
  This is the first line
  >>> with open("New_file.txt", "a") as file:
  ...     file.write("This is the second line")
  ...
  23
  >>> file = open("New_file.txt")
  >>> print(file.read())
  This is the first lineThis is the second line
  >>> with open("New_file.txt", "a") as file:
  ...     file.write("\nThis is the third line")
  ...
  23
  >>> file = open("New_file.txt")
  >>> print(file.read())
  This is the first lineThis is the second line
  This is the third line
  
  ```

  #### Working with Files

  ```python
  >>> import os
  >>> os.remove("New_file.txt")
  >>> os.rename("haiku.txt", "Haiku.txt")
  >>> os.path.exists("haiku.txt")
  False
  >>> os.path.exists("Haiku.txt")
  True
  
  >>> os.path.getsize("Haiku.txt")
  68
  >>> os.path.getmtime("Haiku.txt")
  1612238762.5619702
  >>> import datetime
  >>> timestamp = os.path.getmtime("Haiku.txt")
  >>> datetime.datetime.fromtimestamp(timestamp)
  datetime.datetime(2021, 2, 2, 13, 6, 2, 561970)
  >>> os.path.abspath("Haiku.txt")
  '/home/admin/SelfLearning/Haiku.txt'Directories
  ```

  ```python
  >>> print(os.getcwd())
  /home/admin/SelfLearning
  >>> os.mkdir("New_test_folder")
  >>> os.chdir("New_test_folder")
  >>> print(os.getcwd())
  /home/admin/SelfLearning/New_test_folder
  >>> os.chdir("/home/admin/SelfLearning")
  >>> os.rmdir("New_test_folder")
  ```

  ```python
  >>> import os
  >>> os.mkdir("test_folder")
  >>> os.chdir("test_folder")
  >>> file1 = open("New_file1", "w")
  >>> file2 = open("New_file2", "w")
  >>> os.mkdir("New_folder")
  >>> os.getcwd()
  '/home/admin/SelfLearning/test_folder'
  >>> os.chdir("/home/admin/SelfLearning/")
  >>> os.getcwd()
  '/home/admin/SelfLearning'
  >>> os.listdir("test_folder")
  ['New_file1', 'New_file2', 'New_folder']
  
  [admin@c-8-client SelfLearning]$ cat check_FileOrDirectory.py
  #!/usr/bin/env python3
  
  import os
  dir = "test_folder"
  for name in os.listdir(dir):
      fullname = os.path.join(dir, name)
      if os.path.isdir(fullname):
          print("{} is a directory.".format(fullname))
      else:
          print("{} is a file".format(fullname))
          
  [admin@c-8-client SelfLearning]$ ./check_FileOrDirectory.py
  test_folder/New_file1 is a file
  test_folder/New_file2 is a file
  test_folder/New_folder is a directory.
  
  ```

#### Reading and Writing CSV File

```python
[admin@c-8-client SelfLearning]$ cat test.csv
Sarah Brown, 090-291-222, Programmer
Luis Antio, 121-221-920, System Administrator

>>> import csv
>>> f = open("test.csv")
>>> f_csv = csv.reader(f)
>>> for row in f_csv:
...     name, phone, role = row
...     print("name: {}, phone: {}, role: {}".format(name, phone, role))
...
name: Sarah Brown, phone:  090-291-222, role:  Programmer
name: Luis Antio, phone:  121-221-920, role:  System Administrator
>>> f.close()
```

```python
>>> hosts = [["workstation.local", "192.12.1.23"], ["webserver.cloud", "10.2.34.22"]]
>>> with open("hosts.csv", "w") as hosts_csv:
...     writer = csv.writer(hosts_csv)
...     writer.writerows(hosts)
...
>>> file = open("hosts.csv")
>>> print(file.read().strip())
workstation.local,192.12.1.23
webserver.cloud,10.2.34.22
>>> file.close()

```

```python
[admin@c-8-client SelfLearning]$ cat software.csv
name,version,status,users
Max,3.33,production,232
Luis,3.34,beta,222

>>> with open("software.csv") as file:
...     reader = csv.DictReader(file)
...     for row in reader:
...         print(("{} has {} users").format(row["name"], row["users"]))
...
Max has 232 users
Luis has 222 users

```

#### Reading and Writing CSV Files with Dictionaries 

```python
>>> users = [{"name": "Sol Mansi", "username": "solm", "department": "IT"}, 
{"name": "Lio Nelson", "username": "lion", "department": "User Experience Research"}]

>>> keys = ["name", "username", "department"]
>>> with open("by_department.csv", "w") as by_department:
...     writer = csv.DictWriter(by_department, fieldnames=keys)
...     writer.writeheader()
...     writer.writerows(users)
...
26

>>> file=open("by_department.csv")
>>> print(file.read().strip())
name,username,department
Sol Mansi,solm,IT
Lio Nelson,lion,User Experience Research

```



### Big Quiz

```bash
student-04-09e0fc9b227d@linux-instance:~/scripts$ cat ../data/employees.csv
Full Name, Username, Department
Audrey Miller, audrey, Development
Arden Garcia, ardeng, Sales
Bailey Thomas, baileyt, Human Resources
Blake Sousa, sousa, IT infrastructure
Cameron Nguyen, nguyen, Marketing
Charlie Grey, greyc, Development
Chris Black, chrisb, User Experience Research
Courtney Silva, silva, IT infrastructure
Darcy Johnsonn, darcy, IT infrastructure
Elliot Lamb, elliotl, Development
Emery Halls, halls, Sales
Flynn McMillan, flynn, Marketing
Harley Klose, harley, Human Resources
Jean May Coy, jeanm, Vendor operations
Kay Stevens, kstev, Sales
Lio Nelson, lion, User Experience Research
Logan Tillas, tillas, Vendor operations
Micah Lopes, micah, Development
Sol Mansi, solm, IT infrastructure
```



```python
student-04-09e0fc9b227d@linux-instance:~/scripts$ cat generate_report.py
#!/usr/bin/env python3

import csv

def read_employees(csv_file_location):
    csv.register_dialect('empDialect', skipinitialspace=True, strict=True)
    employee_file = csv.DictReader(open(csv_file_location), dialect = 'empDialect')
    employee_list = []
    for data in employee_file:
        employee_list.append(data)
    return employee_list

employee_list = read_employees('/home/student-04-09e0fc9b227d/data/employees.csv')
print(employee_list)
student-04-09e0fc9b227d@linux-instance:~/scripts$ ./generate_report.py
[{'Username': 'audrey', 'Department': 'Development', 'Full Name': 'Audrey Miller'}, {'Username': 'ardeng', 'Department': 'Sales', 'Full Name': 'Arden Garcia'}, {'Username': 'baileyt', 'Department': 'Human Resources', 'Full Name': 'Bailey Thomas'}, {'Username': 'sousa', 'Department': 'IT infrastructure', 'Full Name': 'Blake Sousa'}, {'Username': 'nguyen', 'Department': 'Marketing', 'Full Name': 'Cameron Nguyen'}, {'Username': 'greyc', 'Department': 'Development', 'Full Name': 'Charlie Grey'}, {'Username': 'chrisb', 'Department': 'User Experience Research', 'Full Name': 'Chris Black'}, {'Username': 'silva', 'Department': 'IT infrastructure', 'Full Name': 'Courtney Silva'}, {'Username': 'darcy', 'Department': 'IT infrastructure', 'Full Name': 'Darcy Johnsonn'}, {'Username': 'elliotl', 'Department': 'Development', 'Full Name': 'Elliot Lamb'}, {'Username': 'halls', 'Department': 'Sales', 'Full Name': 'Emery Halls'}, {'Username': 'flynn', 'Department': 'Marketing', 'Full Name': 'Flynn McMillan'}, {'Username': 'harley', 'Department': 'Human Resources', 'Full Name': 'Harley Klose'}, {'Username': 'jeanm', 'Department': 'Vendor operations', 'Full Name': 'Jean May Coy'}, {'Username': 'kstev', 'Department': 'Sales', 'Full Name': 'Kay Stevens'}, {'Username': 'lion', 'Department': 'User Experience Research', 'Full Name': 'Lio Nelson'}, {'Username': 'tillas', 'Department': 'Vendor operations', 'Full Name': 'Logan Tillas'}, {'Username': 'micah', 'Department': 'Development', 'Full Name': 'Micah Lopes'}, {'Username': 'solm', 'Department': 'IT infrastructure', 'Full Name': 'Sol Mansi'}]

```

```python
student-04-09e0fc9b227d@linux-instance:~/scripts$ cat generate_report.py
#!/usr/bin/env python3

import csv

def read_employees(csv_file_location):
    csv.register_dialect('empDialect', skipinitialspace=True, strict=True)
    employee_file = csv.DictReader(open(csv_file_location), dialect = 'empDialect')
    employee_list = []
    for data in employee_file:
        employee_list.append(data)
    return employee_list

employee_list = read_employees('/home/student-04-09e0fc9b227d/data/employees.csv')
#print(employee_list)

def process_data(employee_list):
    department_list = []
    for employee_data in employee_list:
        department_list.append(employee_data['Department'])
    department_data = {}
    for department_name in set(department_list):
        department_data[department_name] = department_list.count(department_name)
    return department_data

dictionary = process_data(employee_list)
print(dictionary)
student-04-09e0fc9b227d@linux-instance:~/scripts$ ./generate_report.py
{'User Experience Research': 2, 'Development': 4, 'IT infrastructure': 4, 'Marketing': 2, 'Sales': 3, 'Human Resources': 2, 'Vendor operations': 2}

```



```python
student-04-09e0fc9b227d@linux-instance:~/scripts$ cat ./generate_report.py
#!/usr/bin/env python3

import csv

def read_employees(csv_file_location):
    csv.register_dialect('empDialect', skipinitialspace=True, strict=True)
    employee_file = csv.DictReader(open(csv_file_location), dialect = 'empDialect')
    employee_list = []
    for data in employee_file:
        employee_list.append(data)
    return employee_list

employee_list = read_employees('/home/student-04-09e0fc9b227d/data/employees.csv')
#print(employee_list)

def process_data(employee_list):
    department_list = []
    for employee_data in employee_list:
        department_list.append(employee_data['Department'])
    department_data = {}
    for department_name in set(department_list):
        department_data[department_name] = department_list.count(department_name)
    return department_data

dictionary = process_data(employee_list)
#print(dictionary)

def write_report(dictionary, report_file):
    with open(report_file, "w+") as f:
        for k in sorted(dictionary):
            f.write(str(k)+':'+str(dictionary[k])+'\n')
    f.close()

write_report(dictionary, '/home/student-04-09e0fc9b227d/data/report.txt')
student-04-09e0fc9b227d@linux-instance:~/scripts$ cat ../data/report.txt
Development:4
Human Resources:2
IT infrastructure:4
Marketing:2
Sales:3
User Experience Research:2
Vendor operations:2
```











```python
import os
def create_python_script(filename):
    comments = "# Start of a new Python program"
    with open(filename, "w") as filename1:
        filename1.write(comments)
    filesize = os.path.getsize(filename)
    return(filesize)

print(create_python_script("program.py"))
```



```python
import os
def parent_directory():
    # Create a relative path to the parent 
    # of the current working directory 
    relative_parent = os.path.join(os.getcwd(), os.pardir)
    # Return the absolute path of the parent directory
    return os.path.abspath(relative_parent)

print(parent_directory())
```







### Practice Quiz: Reading & Writing CSV Files


Question 1: We're working with a list of flowers and some information about each one. The create_file function writes this information to a CSV file. The contents_of_file function reads this file into records and returns the information in a nicely formatted block. Fill in the gaps of the contents_of_file function to turn the data in the CSV file into a dictionary using DictReader.

```python
import os
import csv
# Create a file with data in it
def create_file(filename):
  with open(filename, "w") as file:
    file.write("name,color,type\n")
    file.write("carnation,pink,annual\n")
    file.write("daffodil,yellow,perennial\n")
# Read the file contents and format the information about each row
def contents_of_file(filename):
  return_string = ""
  # Call the function to create the file 
  create_file(filename)
  # Open the file
  with open(filename) as file:
    # Read the rows of the file into a dictionary
    f = csv.DictReader(file)
    # Process each item of the dictionary
    for row in f:
      return_string += "a {} {} is {}\n".format(row["color"], row["name"], row["type"])
  return return_string
#Call the function
print(contents_of_file("flowers.csv"))
```


Question 2： Using the CSV file of flowers again, fill in the gaps of the contents_of_file function to process the data without turning it into a dictionary. How do you skip over the header record with the field names?

```python
import os
import csv

# Create a file with data in it
def create_file(filename):
  with open(filename, "w") as file:
    file.write("name,color,type\n")
    file.write("carnation,pink,annual\n")
    file.write("daffodil,yellow,perennial\n")
    file.write("iris,blue,perennial\n")
    file.write("poinsettia,red,perennial\n")
    file.write("sunflower,yellow,annual\n")

# Read the file contents and format the information about each row
def contents_of_file(filename):
  return_string = ""

  # Call the function to create the file 
  create_file(filename)

  # Open the file
  with open(filename) as f:
    # Read the rows of the file
    rows = csv.reader(f)
    headers = next(rows)
    # Process each row
    for row in rows:
      name, color, ty = row
      # Format the return string for data rows only
      return_string += "a {} {} is {}\n".format(color, name, ty)
  return return_string

#Call the function
print(contents_of_file("flowers.csv"))
```











### Regular Expression

#### re module example

```python
import re 
log = "July 31 07:19:02 mycomputer bad_process[12345]: ERROR Performing package upgrade"
regex = r"\[(\d+)\]"
result = re.search(regex, log)
print(result[1])
```

#### grep command under Linux CLI

```bash
[root@c7-server ~]# grep l.rts /usr/share/dict/words
alerts
blurts
#...省略
[root@c7-server ~]# grep l..ts /usr/share/dict/words
ablauts
aerialists
#...省略
[root@c7-server ~]# grep ^fruit /usr/share/dict/words
fruit
fruitade
fruitage
#...省略
[root@c7-server ~]# grep cat$ /usr/share/dict/words
avocat
bearcat
#...省略
```

#### Simple Matching in Python

```python
>>> import re
>>> result = re.search(r"aza", "plaza")
>>> print(result)
<re.Match object; span=(2, 5), match='aza'>
>>> result = re.search(r"aza", "bazaar")
>>> print(result)
<re.Match object; span=(1, 4), match='aza'>
>>> result = re.search(r"aza", "plazza")
>>> print(result)
None
>>> print(re.search(r"^x", "xenon"))
<re.Match object; span=(0, 1), match='x'>
>>> print(re.search(r"p.ng", "penguin"))
<re.Match object; span=(0, 4), match='peng'>
>>> print(re.search(r"p.ng", "sponge"))
<re.Match object; span=(1, 5), match='pong'>
>>> print(re.search(r"p.ng", "clapping"))
<re.Match object; span=(4, 8), match='ping'>
>>> print(re.search(r"p.ng", "Pangaea", re.IGNORECASE))
<re.Match object; span=(0, 4), match='Pang'>
```

##### Wildcard

```python
>>> print(re.search(r"[a-z]way", "The end of the highway"))
<re.Match object; span=(18, 22), match='hway'>

>>> print(re.search("cloud[a-zA-Z0-0]", "cloudy"))     #[a-zA-Z0-0]
<re.Match object; span=(0, 6), match='cloudy'>
>>> print(re.search("cloud[a-zA-Z0-0]", "cloud0"))
<re.Match object; span=(0, 6), match='cloud0'>

#Question: Fill in the code to check if the text passed contains punctuation symbols: commas, periods, colons, semicolons, question marks, and exclamation points.
import re
def check_punctuation (text):
    result = re.search(r"[,.:;?!]", text)
    return result != None
print(check_punctuation("This is a sentence that ends with a period.")) # True
print(check_punctuation("This is a sentence fragment without a period")) # False

#Exclude排除
>>> print(re.search(r"[^a-zA-Z]", "This is a sentence with spaces."))
<re.Match object; span=(4, 5), match=' '>
>>> print(re.search(r"[^a-zA-Z ]", "This is a sentence with spaces."))
<re.Match object; span=(30, 31), match='.'>
>>> print(re.search(r"[^0-9/ ]", "2021/01/24 This is a sentence with spaces."))
<re.Match object; span=(11, 12), match='T'>

#The power of findall()
>>> print(re.search(r"cat|dog", "I like cats"))
<re.Match object; span=(7, 10), match='cat'>
>>> print(re.search(r"cat|dog", "I like dogs"))
<re.Match object; span=(7, 10), match='dog'>
>>> print(re.search(r"cat|dog", "I like both dogs and cats"))
<re.Match object; span=(12, 15), match='dog'>
>>> print(re.findall(r"cat|dog", "I like both dogs and cats"))
['dog', 'cat']
```

##### Repetition Qualifiers

```python
>>> print(re.search(r"Py.*n", "Python Programming"))
<re.Match object; span=(0, 17), match='Python Programmin'>
>>> print(re.search(r"Py[a-z]*n", "Python Programming"))
<re.Match object; span=(0, 6), match='Python'>
#? means either zero or one occurrence of the character before it.
>>> print(re.search(r"p?each", "To each theirown"))    
<re.Match object; span=(3, 7), match='each'>
>>> print(re.search(r"p?each", "I like peaches"))
<re.Match object; span=(7, 12), match='peach'>
```

##### Escaping Characters

```python
>>> print(re.search(r".com", " This is lcom"))
<re.Match object; span=(9, 13), match='lcom'>
# However, we just need an exact output of ".com". So we use backslash to achive this.
>>> print(re.search(r"\.com", " This is lcom"))
None
>>> print(re.search(r"\.com", "mydomain.com"))
<re.Match object; span=(8, 12), match='.com'>

#On top of this, Python also uses the backslash for a few special sequences that we can use to represent predefined sets of characters. For example, \w matches any alphanumeric character including letters, numbers, and underscores. 
>>> print(re.search(r"\w*", "This is an example."))
<re.Match object; span=(0, 4), match='This'>
>>> print(re.search(r"\w*", "And_This_Is_Another."))
<re.Match object; span=(0, 19), match='And_This_Is_Another'>

```



```python
>>> print(re.search(r"A.*a", "Argentina"))
<re.Match object; span=(0, 9), match='Argentina'>
>>> print(re.search(r"A.*a", "Azerbaijan"))
<re.Match object; span=(0, 9), match='Azerbaija'>
>>> print(re.search(r"^A.*a$", "Azerbaijan"))
None

>>> pattern = r"^[a-zA-Z_][a-zA-Z0-9_]*$"
>>> print(re.search(pattern, "_This_is_a_valid_name"))
<re.Match object; span=(0, 21), match='_This_is_a_valid_name'>
>>> print(re.search(pattern, "_This is_a_valid_name"))
None
>>> print(re.search(pattern, "1This_is_a_valid_name"))
None
#Fill in the code to check if the text passed looks like a standard sentence, meaning that it starts with an uppercase letter, followed by at least some lowercase letters or a space, and ends with a period, question mark, or exclamation point. 
import re
def check_sentence(text):
  result = re.search(r"^[A-Z][a-z\s]*[\.\?!]$", text)
  return result != None

print(check_sentence("Is this is a sentence?")) # True
print(check_sentence("is this is a sentence?")) # False
print(check_sentence("Hello")) # False



#Question 3:The contains_acronym function checks the text for the presence of 2 or more characters or digits surrounded by parentheses, with at least the first character in uppercase (if it's a letter), returning True if the condition is met, or False otherwise. For example, "Instant messaging (IM) is a set of communication technologies used for text-based communication" should return True since (IM) satisfies the match conditions." Fill in the regular expression in this function:

import re
def contains_acronym(text):
    pattern = r"\([A-Z0-9][a-zA-Z0-9]*\)"
    result = re.search(pattern, text)
    return result != None

print(contains_acronym("Instant messaging (IM) is a set of communication technologies used for text-based communication")) # True
print(contains_acronym("American Standard Code for Information Interchange (ASCII) is a character encoding standard for electronic communication")) # True
print(contains_acronym("Please do NOT enter without permission!")) # False
print(contains_acronym("PostScript is a fourth-generation programming language (4GL)")) # True
print(contains_acronym("Have fun using a self-contained underwater breathing apparatus (Scuba)!")) # True 
```

### Advanced Regular Express

#### Capturing Groups

```python
>>> result = re.search(r"^(\w*), (\w*)$", "Lovelace, Ada")
>>> print(result)
<re.Match object; span=(0, 13), match='Lovelace, Ada'>

import re
def rearrange_name(name):
  result = re.search(r"^([\w \.-]*), ([\w \.-]*)$", name)
  if result == None:
    return name
  return "{} {}".format(result[2], result[1])

name=rearrange_name("Kennedy, John FFF.")
print(name)
```

#### More on Repetition Qualifiers

```python
>>> print(re.search(r"[a-zA-Z]{5}", "a ghost"))
<re.Match object; span=(2, 7), match='ghost'>
>>> print(re.search(r"[a-zA-Z]{5}", "a scary ghost appeared"))
<re.Match object; span=(2, 7), match='scary'>
>>> print(re.findall(r"[a-zA-Z]{5}", "a scary ghost appeared"))
['scary', 'ghost', 'appea']
>>> print(re.findall(r"\b[a-zA-Z]{5}\b", "a scary ghost appeared"))
['scary', 'ghost']
>>> print(re.findall(r"\w{5,10}", "I really like a strawberries"))
['really', 'strawberri']
>>> print(re.findall(r"\w{5,}", "I really like a strawberries"))
['really', 'strawberries']
>>> print(re.search(r"s\w{,20}", "I really like a strawberries"))
<re.Match object; span=(16, 28), match='strawberries'>


```

#### Extracting a PID Using regexes in Python

```python
import re
def extract_pid(log_line):
    regex = r"\[(\d+)\]"
    result = re.search(regex, log_line)
    if result is None:
        return ""
    return result[1]

log = "This is the fake log [12345]"
print(extract_pid(log))

#Add to the regular expression used in the extract_pid function, to return the uppercase message in parenthesis, after the process id.
import re
def extract_pid(log_line):
    regex = r"\[(\d+)\]\: ([A-Z]*)"
    result = re.search(regex, log_line)
    if result is None:
        return None
    return "{} ({})".format(result[1], result[2])

print(extract_pid("July 31 07:51:48 mycomputer bad_process[12345]: ERROR Performing package upgrade")) # 12345 (ERROR)
print(extract_pid("99 elephants in a [cage]")) # None
```

#### Splitting and Replacing

```python
>>> import re
>>> re.split(r"[.?!]", "One sentence. Another one? And last one!")
['One sentence', ' Another one', ' And last one', '']
>>> re.split(r"([.?!])", "One sentence. Another one? And last one!")
['One sentence', '.', ' Another one', '?', ' And last one', '!', '']

>>> re.sub(r"^([\w .-]*), ([\w .-]*)$", r"\2 \1", "Lovelace, Ada")
'Ada Lovelace'

>>> re.split(r"the|a", "One sentence. Another one? And the last one!")
['One sentence. Ano', 'r one? And ', ' l', 'st one!']
```

### Managing Data and Processes

```python
#使用input进行交互式输入：
def to_seconds(hours, minutes, seconds):
    return hours*3600+minutes*60+seconds
print("Welcome to this time converter")

cont = "y"
while(cont.lower() == "y"):
    hours = int(input("Enter the number of hours: "))
    minutes = int(input("Enter the number of minutes: "))
    seconds = int(input("Enter the number of seconds: "))

    print("That's {} seconds".format(to_seconds(hours, minutes, seconds)))
    print()
    cont = input("Do you want to do another conversion? [y to continue]")
print("Good bye!")
```

##### Environment Variables

```python
>>> os.environ.get("HOME")
'/home/anthony'
>>> os.environ.get("SHELL")
'/bin/bash'
```

##### Command-Line Arguments and Exit Status

```python
[root@c-8-client admin]# nano test.py
#!/usr/bin/env python3
import os
import sys

filename=sys.argv[1]

if not os.path.exists(filename):
    with open(filename, "w") as f:
        f.write("New file created\n")
else:
    print("Error, the file {} already existes!".format(filename))
    sys.exit(1)

[root@c-8-client admin]# ./test.py example
[root@c-8-client admin]# ls -l
-rw-r--r--. 1 root  root   17 Jan 27 12:36 example
-rwxrwxrwx. 1 admin admin 262 Jan 27 12:36 test.py
[root@c-8-client admin]# cat example
New file created
[root@c-8-client admin]# ./test.py example
Error, the file example already existes!
[root@c-8-client admin]# echo $?
1
```

```python
>>> my_number = input('Please Enter a Number: \n')
Please Enter a Number: 
123 + 1
>>> print(my_number)
123 + 1
>>> eval(my_number)
124
```

#### Running System Commands in Python

```python
>>> import subprocess
>>> subprocess.run(["date"])
Sat Jan 30 16:42:05 JST 2021
CompletedProcess(args=['date'], returncode=0)
>>> subprocess.run(["sleep", "2"])
CompletedProcess(args=['sleep', '2'], returncode=0)

>>> result = subprocess.run(["ls", "this_file_does_not_exist"])
ls: cannot access 'this_file_does_not_exist': No such file or directory
>>> print(result.returncode)
2
```

#### Obtaining the Output of a System Command

```python
>>> import subprocess
>>> result = subprocess.run(["host", "8.8.8.8"], capture_output=True)
>>> print(result.returncode)
0
>>> print(result.stdout)
b'8.8.8.8.in-addr.arpa domain name pointer dns.google.\n'
>>> print(result.stdout.decode().split())
['8.8.8.8.in-addr.arpa', 'domain', 'name', 'pointer', 'dns.google.']

>>> result = subprocess.run(["rm", "does_not_exist"], capture_output=True)
>>> print(result.returncode)
1
>>> print(result.stdout)
b''
>>> print(result.stderr)
b"rm: cannot remove 'does_not_exist': No such file or directory\n"
```

#### Filtering Log Files with Regular Expressions

```python
[root@c-8-client ~]# cat testlog
Jul 6 computer.name CRON[92829]: USER (good_user)
Jul 6 computer.name CRON[72728]: USER (naughty_user)
[root@c-8-client ~]# cat test1.py
#!/usr/bin/env python3
import re
import sys
logfile = sys.argv[1]
with open(logfile) as f:
    for line in f:
        if "CRON" not in line:
            continue
        pattern = r"USER \((\w+)\)$"
        result = re.search(pattern, line)
        print(result[1])

[root@c-8-client ~]# ./test1.py testlog
good_user
naughty_user

#We're using the same syslog, and we want to display the date, time, and process id that's inside the square brackets. We can read each line of the syslog and pass the contents to the show_time_of_pid function. Fill in the gaps to extract the date, time, and process id from the passed line, and return this format: Jul 6 14:01:23 pid:29440.
import re
def show_time_of_pid(line):
    pattern = ___ #更改处
    result = re.search(pattern, line)
    return "{}pid:{}".format(result[1], result[2])

print(show_time_of_pid("Jul 6 14:01:23 computer.name CRON[29440]: USER (good_user)")) # Jul 6 14:01:23 pid:29440
print(show_time_of_pid("Jul 6 14:02:08 computer.name jam_tag=psim[29187]: (UUID:006)")) # Jul 6 14:02:08 pid:29187
print(show_time_of_pid("Jul 6 14:02:09 computer.name jam_tag=psim[29187]: (UUID:007)")) # Jul 6 14:02:09 pid:29187
print(show_time_of_pid("Jul 6 14:03:01 computer.name CRON[29440]: USER (naughty_user)")) # Jul 6 14:03:01 pid:29440

A:    pattern = r"(^\w+ \d \d+:\d+:\d+ )computer.name \w+=?\w+\[(\d+)\]"
```

#### Making Sense out of the Data

```python
>>> usernames = {}
>>> name = "good_user"
>>> usernames[name] = usernames.get(name, 0) +1
>>> print(usernames)
{'good_user': 1}
>>> usernames[name] = usernames.get(name, 0) +1
>>> print(usernames)
{'good_user': 2}

```



### Testing in Python

#### Writing Unit Tests in Python

```python
[admin@c-8-client SelfLearning]$ cat rearrange.py
#!/usr/bin/env python3

import re

def rearrange_name(name):
        result =  re.search(r"^([\w .]*), ([\w .]*)$", name)
        return "{} {}".format(result[2], result[1])
    
[admin@c-8-client SelfLearning]$ cat rearrange_test.py
#!/usr/bin/env python3

from rearrange import rearrange_name
import unittest

class TestRearrange(unittest.TestCase):
        def test_basic(self):
                testcase = "Loveplace, Ada"
                expected = "Ada Loveplace"
                self.assertEqual(rearrange_name(testcase), expected)

unittest.main()

[admin@c-8-client SelfLearning]$ ./rearrange_test.py
.
----------------------------------------------------------------------
Ran 1 test in 0.001s

OK
```

#### Edge Cases

```python
[admin@c-8-client SelfLearning]$ cat rearrange.py
#!/usr/bin/env python3

import re

def rearrange_name(name):
        result =  re.search(r"^([\w .]*), ([\w .]*)$", name)
        if result is None:   #新增
                return ""   #新增
        return "{} {}".format(result[2], result[1])
[admin@c-8-client SelfLearning]$ cat rearrange_test.py
#!/usr/bin/env python3

from rearrange import rearrange_name
import unittest

class TestRearrange(unittest.TestCase):
        def test_basic(self):
                testcase = "Loveplace, Ada"
                expected = "Ada Loveplace"
                self.assertEqual(rearrange_name(testcase), expected)

        def test_empty(self):   #新增
                testcase = ""   #新增
                expected = ""   #新增
                self.assertEqual(rearrange_name(testcase), expected)  #新增

unittest.main()
[admin@c-8-client SelfLearning]$ ./rearrange_test.py
..
----------------------------------------------------------------------
Ran 2 tests in 0.001s

OK

```

#### Additional Test Cases

```python
[admin@c-8-client SelfLearning]$ cat rearrange.py
#!/usr/bin/env python3

import re

def rearrange_name(name):
        result =  re.search(r"^([\w .]*), ([\w .]*)$", name)
        if result is None:
                return name  #修改行
        return "{} {}".format(result[2], result[1])
    
[admin@c-8-client SelfLearning]$ cat rearrange_test.py
#!/usr/bin/env python3

from rearrange import rearrange_name
import unittest

class TestRearrange(unittest.TestCase):
        def test_basic(self):
                testcase = "Loveplace, Ada"
                expected = "Ada Loveplace"
                self.assertEqual(rearrange_name(testcase), expected)

        def test_empty(self):
                testcase = ""
                expected = ""
                self.assertEqual(rearrange_name(testcase), expected)

        def test_doublename(self):    #增加校验
                testcase = "Jay, Luis M."
                expected = "Luis M. Jay"
                self.assertEqual(rearrange_name(testcase), expected)

        def test_singlename(self):   #增加校验
                testcase = "Elfa"
                expected = "Elfa"
                self.assertEqual(rearrange_name(testcase), expected)

unittest.main()

[admin@c-8-client SelfLearning]$ ./rearrange_test.py
....
----------------------------------------------------------------------
Ran 4 tests in 0.001s

OK
```

#### Unit Test Cheat-Sheet

------

Frankly, the unit testing library for Python is fairly well documented, but it can be a bit of a dry read. Instead, we suggest covering the core module concepts, and then reading in more detail later.

##### Best of Unit Testing Standard Library Module

Understand a Basic Example:

- https://docs.python.org/3/library/unittest.html#basic-example

Understand how to run the tests using the Command Line:

- https://docs.python.org/3/library/unittest.html#command-line-interface

Understand various Unit Test Design Patterns:

- https://docs.python.org/3/library/unittest.html#organizing-test-code

- Understand the uses of setUp, tearDown; setUpModule and tearDownModule

Understand more specific assertions such as assertRaises

- https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertRaises

##### Understand basic assertions:

| **Method**                                                   | **Checks that**      | **New in** |
| :----------------------------------------------------------- | :------------------- | :--------- |
| [assertEqual(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertEqual) | a == b               |            |
| [assertNotEqual(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertNotEqual) | a != b               |            |
| [assertTrue(x)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertTrue) | bool(x) is True      |            |
| [assertFalse(x)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertFalse) | bool(x) is False     |            |
| [assertIs(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIs) | a is b               | 3.1        |
| [assertIsNot(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsNot) | a is not b           | 3.1        |
| [assertIsNone(x)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsNone) | x is None            | 3.1        |
| [assertIsNotNone(x)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsNotNone) | x is not None        | 3.1        |
| [assertIn(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIn) | a in b               | 3.1        |
| [assertNotIn(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertNotIn) | a not in b           | 3.1        |
| [assertIsInstance(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsInstance) | isinstance(a, b)     | 3.2        |
| [assertNotIsInstance(a, b)](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertNotIsInstance) | not isinstance(a, b) | 3.2        |

#### More About Tests

------

Check out the following links for more information:

- https://landing.google.com/sre/sre-book/chapters/monitoring-distributed-systems/
- https://landing.google.com/sre/sre-book/chapters/testing-reliability/

- https://testing.googleblog.com/2007/10/performance-testing.html
- https://www.guru99.com/smoke-testing.html
- https://www.guru99.com/exploratory-testing.html
- https://testing.googleblog.com/2008/09/test-first-is-fun_08.html

#### Raising Errors

```python
[admin@c-8-client SelfLearning]$ cat validations.py
#!/usr/bin/env python3

def validate_user(username, minlen):
    assert type(username) == str, "username must be a string"
    if minlen < 1:
        raise ValueError("minlen must be at least 1")
    if len(username) < minlen:
        return False
    if not username.isalnum():
        return False
    return True

[admin@c-8-client SelfLearning]$ python3.8
Python 3.8.1 (default, Jan 30 2021, 17:15:53)
[GCC 8.3.1 20191121 (Red Hat 8.3.1-5)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from validations import validate_user
>>> validate_user("", 1)
False
>>> validate_user("myname", 1)
True
>>> validate_user(2, 1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/admin/SelfLearning/validations.py", line 4, in validate_user
    assert type(username) == str, "username must be a string"
AssertionError: username must be a string
>>> validate_user("", -1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/admin/SelfLearning/validations.py", line 6, in validate_user
    raise ValueError("minlen must be at least 1")
ValueError: minlen must be at least 1
```

#### Testing for Expected Errors

```python
[admin@c-8-client SelfLearning]$ cat validations.py
#!/usr/bin/env python3
def validate_user(username, minlen):
    assert type(username) == str, "username must be a string"
    if minlen < 1:
        raise ValueError("minlen must be at least 1")
    if len(username) < minlen:
        return False
    if not username.isalnum():
        return False
    return True

[admin@c-8-client SelfLearning]$ cat validations_test.py
#!/usr/bin/env python3
import unittest
from validations import validate_user

class TestValidateUser(unittest.TestCase):
        def test_valid(self):
                self.assertEqual(validate_user("validuser", 3), True)
        def test_too_short(self):
                self.assertEqual(validate_user("inv", 5), False)
        def test_invalid_characters(self):
                self.assertEqual(validate_user("invalid_user", 1), False)
        def test_invalid_minlen(self):
                self.assertRaises(ValueError, validate_user, "user", -1)

#Run the tests
unittest.main()

[admin@c-8-client SelfLearning]$ ./validations_test.py -v
test_invalid_characters (__main__.TestValidateUser) ... ok
test_invalid_minlen (__main__.TestValidateUser) ... ok
test_too_short (__main__.TestValidateUser) ... ok
test_valid (__main__.TestValidateUser) ... ok
----------------------------------------------------------------------
Ran 4 tests in 0.001s

OK
```

#### Handling Errors Cheat-Sheet

------

Raise allows you to throw an exception at any time.

- https://docs.python.org/3/tutorial/errors.html#raising-exceptions

Assert enables you to verify if a certain condition is met and throw an exception if it isn’t.

- [https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement](https://docs.python.org/2/reference/simple_stmts.html#the-assert-statement)
- https://stackoverflow.com/questions/5142418/what-is-the-use-of-assert-in-python

The standard library documentation is kind of unclear. Basically `assert <something false>` will raise AssertionError, which the caller may need to handle.

In the try clause, all statements are executed until an exception is encountered.

- [https://docs.python.org/3/tutorial/errors.html#handling-exceptions](https://docs.python.org/2/tutorial/errors.html#handling-exceptions)

Except is used to catch and handle the exception(s) that are encountered in the try clause.

- https://docs.python.org/3/library/exceptions.html#bltin-exceptions

Other interesting Exception handling readings:

- https://doughellmann.com/blog/2009/06/19/python-exception-handling-techniques/



### Bash scripting

#### Redirecting Streams







```python
[admin@c-8-client ~]$ cat stdout_example.py
#!/usr/bin/env python3
print("This is just a test text.")
[admin@c-8-client ~]$ ./stdout_example.py > new_test_file.txt
[admin@c-8-client ~]$ cat new_test_file.txt
This is just a test text.
[admin@c-8-client ~]$ ./stdout_example.py >> new_test_file.txt
[admin@c-8-client ~]$ cat new_test_file.txt
This is just a test text.
This is just a test text.

[admin@c-8-client SelfLearning]$ cat ./streams_err.py
#!/usr/bin/env python3
data = input("This will come from STDIN: ")
print("Now we write it to STDOUT: " + data)
raise ValueError("Now we generate an error to STDERR")
[admin@c-8-client SelfLearning]$ ./streams_err.py < new_test_file.txt
This will come from STDIN: Now we write it to STDOUT: This is just a test text.
Traceback (most recent call last):
  File "./streams_err.py", line 5, in <module>
    raise ValueError("Now we generate an error to STDERR")
ValueError: Now we generate an error to STDERR

[admin@c-8-client SelfLearning]$ ./streams_err.py < new_test_file.txt 2> error_file.txt
This will come from STDIN: Now we write it to STDOUT: This is just a test text.
[admin@c-8-client SelfLearning]$ cat error_file.txt
Traceback (most recent call last):
  File "./streams_err.py", line 5, in <module>
    raise ValueError("Now we generate an error to STDERR")
ValueError: Now we generate an error to STDERR

[admin@c-8-client SelfLearning]$ echo "This is also a test file" > test2.txt
[admin@c-8-client SelfLearning]$ cat test2.txt
This is also a test file
[admin@c-8-client SelfLearning]$ echo "This is also a test file" >> test2.txt
[admin@c-8-client SelfLearning]$ cat test2.txt
This is also a test file
This is also a test file

```

#### Pipes and Pipelines

```python
[admin@c-8-client SelfLearning]$ cat haiku.txt
advance your career,
automatting with Python,
it's so fun to learn.

[admin@c-8-client SelfLearning]$ cat capitalize.py
#!/usr/bin/env python3
import sys
for line in sys.stdin:
    print(line.strip().capitalize())
[admin@c-8-client SelfLearning]$ cat haiku.txt | ./capitalize.py
Advance your career,
Automatting with python,
It's so fun to learn.

[admin@c-8-client SelfLearning]$ ./capitalize.py < haiku.txt
Advance your career,
Automatting with python,
It's so fun to learn.

```

#### Signalling Processes

```bash
1. CTRL Z
[admin@c-8-client SelfLearning]$ ping www.google.com
PING www.google.com (172.217.175.36) 56(84) bytes of data.
64 bytes from nrt20s19-in-f4.1e100.net (172.217.175.36): icmp_seq=1 ttl=119 time=12.5 ms
64 bytes from nrt20s19-in-f4.1e100.net (172.217.175.36): icmp_seq=2 ttl=119 time=11.2 ms
64 bytes from nrt20s19-in-f4.1e100.net (172.217.175.36): icmp_seq=3 ttl=119 time=11.6 ms
^Z
[1]+  Stopped                 ping www.google.com  

2. fg
[admin@c-8-client SelfLearning]$ fg
ping www.google.com
64 bytes from nrt20s19-in-f4.1e100.net (172.217.175.36): icmp_seq=4 ttl=119 time=11.7 ms
64 bytes from nrt20s19-in-f4.1e100.net (172.217.175.36): icmp_seq=5 ttl=119 time=11.5 ms

3. CTRL C
^C
--- www.google.com ping statistics ---
6 packets transmitted, 5 received, 16.6667% packet loss, time 43ms
rtt min/avg/max/mdev = 11.202/11.711/12.508/0.438 ms
[admin@c-8-client SelfLearning]$

```

```bash
[root@c-8-client SelfLearning]# ps aux
root      131667  0.0  0.2  36620  4008 pts/0    S+   13:28   0:00 ping www.google.com
root      131668  0.0  0.2  57820  3844 pts/1    R+   13:28   0:00 ps aux
[root@c-8-client SelfLearning]# kill 131667

[root@c-8-client admin]# ping www.google.com
PING www.google.com (216.58.197.164) 56(84) bytes of data.
64 bytes from nrt12s02-in-f4.1e100.net (216.58.197.164): icmp_seq=1 ttl=119 time=12.8 ms
...
64 bytes from nrt12s02-in-f4.1e100.net (216.58.197.164): icmp_seq=11 ttl=119 time=11.5 ms
Terminated

```



#### Redirections, Pipes and Signals

------

##### Managing streams

These are the redirectors that we can use to take control of the streams of our programs

- command **>** file: redirects standard output, overwrites file
- command **>>** file: redirects standard output, appends to file
- command **<** file: redirects standard input from file
- command **2>** file: redirects standard error to file
- command1 **|** command2: connects the output of command1 to the input of command2

##### Operating with processes

These are some commands that are useful to know in Linux when interacting with processes. Not all of them are explained in videos, so feel free to investigate them on your own.

- **ps:** lists the processes executing in the current terminal for the current user

- **ps** ax: lists all processes currently executing for all users  
- **ps** e: shows the environment for the processes listed  

- **kill** PID: sends the SIGTERM signal to the process identified by PID
- **fg**: causes a job that was stopped or in the background to return to the foreground
- **bg:** causes a job that was stopped to go to the background
- **jobs:** lists the jobs currently running or stopped

- **top:** shows the processes currently using the most CPU time (press "q" to quit)  

#### Creating Bash Script

```bash
[root@c-8-client SelfLearning]# cat bash_test.sh
#!/bin/bash
line="---------------------------------"
echo "Starting at: $(date)"; echo $line

echo "UPTIME"; uptime; echo $line

echo "WHO"; who; echo $line

sleep 10

echo "Finishing at: $(date)"; echo $line

[root@c-8-client SelfLearning]# ./bash_test.sh
Starting at: Tue Feb  2 15:21:25 JST 2021
---------------------------------
UPTIME
 15:21:25 up 2 days, 23:29,  2 users,  load average: 0.34, 0.10, 0.09
---------------------------------
WHO
admin    tty2         2020-11-17 17:27 (tty2)
admin    pts/1        2021-02-02 10:41 (192.168.150.87)
---------------------------------
Finishing at: Tue Feb  2 15:21:35 JST 2021
---------------------------------
```

#### Conditional Execution in Bash

```bash
[root@c-8-client SelfLearning]# cat check_localhost.sh
#!/bin/bash

if grep "127.0.0.1" /etc/hosts; then
        echo "Everything ok"
else
        echo "ERROR! 127.0.0.1 is not in /etc/hosts"
fi
[root@c-8-client SelfLearning]# ./check_localhost.sh
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
Everything ok

[root@c-8-client SelfLearning]# if test -n "$PATH"; then echo "Your path is not empty"; fi
Your path is not empty
[root@c-8-client SelfLearning]# if [ -n "$PATH" ]; then echo "Your path is not empty"; fi
Your path is not empty
```

#### Bash Scripting Resources

------

Check out the following links for more information:

- https://ryanstutorials.net/bash-scripting-tutorial/
- https://linuxconfig.org/bash-scripting-tutorial-for-beginners
- [https://www.shellscript.sh](https://www.shellscript.sh/)

#### While Loops in Bash Scripts

```
[root@c-8-client SelfLearning]# cat while_test.sh
#!/bin/bash

n=1
while [ $n -le 5 ]; do
        echo "Iteration number $n"
        ((n+=1))
done
[root@c-8-client SelfLearning]# ./while_test.sh
Iteration number 1
Iteration number 2
Iteration number 3
Iteration number 4
Iteration number 5
```

```bash
[root@c-8-client SelfLearning]# cat ./random_exit.py
#!/usr/bin/env python3
import sys
import random
value = random.randint(0, 3)
print("Returning: " + str(value))
sys.exit(value)

[root@c-8-client SelfLearning]# cat retry_test.sh
#!/bin/bash
n=0
command=$1
while ! $command && [ $n -le 5 ]; do
        sleep $n
        ((n+=1))
        echo "Retry #$n"
done;

[root@c-8-client SelfLearning]# ./retry_test.sh ./random_exit.py
Returning: 3
Retry #1
Returning: 1
Retry #2
Returning: 1
Retry #3
Returning: 0
[root@c-8-client SelfLearning]#
```

#### For Loops in Bash Scripts

```bash
[admin@c-8-client for_loop_test]$ ls *.HTM
a.HTM  b.HTM  c.HTM
[admin@c-8-client for_loop_test]$ basename a.HTM .HTM
a

[admin@c-8-client for_loop_test]$ cat rename.sh
#!/bin/bash
for file in *.HTM; do
        name=$(basename "$file" .HTM)
        echo mv "$file" "$name.html"
done
[admin@c-8-client for_loop_test]$ ./rename.sh
mv a.HTM a.html
mv b.HTM b.html
mv c.HTM c.html
[admin@c-8-client for_loop_test]$ ls
a.HTM  b.HTM  c.HTM  rename.sh

[admin@c-8-client for_loop_test]$ nano rename.sh
[admin@c-8-client for_loop_test]$ cat rename.sh
#!/bin/bash
for file in *.HTM; do
        name=$(basename "$file" .HTM)
        mv "$file" "$name.html"
done
[admin@c-8-client for_loop_test]$ ./rename.sh
[admin@c-8-client for_loop_test]$ ls
a.html  b.html  c.html  rename.sh

```

```bash
#The scenario:Your coworker Jane Doe currently has the username "jane" but she needs to it to "jdoe" to comply with your company's naming policy. This username change has already been done. However, some files that were named with Jane's previous username "jane" haven't been updated. For example, "jane_profile_07272018.doc" needs to be updated to "jdoe_profile_07272018.doc".

student-03-e2f6cf27da1b@linux-instance:~/data$ grep ' jane ' ./list.txt
001 jane /data/jane_profile_07272018.doc
005 jane /data/jane_pic_07282018.jpg
008 jane /data/jane_contact_07292018.csv
student-03-e2f6cf27da1b@linux-instance:~/data$ grep " jane " ./list.txt | cut -d' ' -f 3
/data/jane_profile_07272018.doc
/data/jane_pic_07282018.jpg
/data/jane_contact_07292018.csv

student-03-e2f6cf27da1b@linux-instance:~/scripts$ cat findJane.sh
#!/bin/bash

> oldFiles.txt

if test -e ~/data/jane_profile_07272018.doc; then echo ~/data/jane_profile_07272018.doc >> oldFiles.txt; fi
if test -e ~/data/jane_pic_07282018.jpg; then echo ~/data/jane_pic_07282018.jpg >> oldFiles.txt; fi
if test -e ~/data/jane_contact_07292018.csv; then echo ~/data/jane_contact_07292018.csv >> oldFiles.txt; fi
student-03-e2f6cf27da1b@linux-instance:~/scripts$ cat oldFiles.txt
/home/student-03-e2f6cf27da1b/data/jane_profile_07272018.doc
/home/student-03-e2f6cf27da1b/data/jane_contact_07292018.csv
student-03-e2f6cf27da1b@linux-instance:~/scripts$ pwd
/home/student-03-e2f6cf27da1b/scripts
student-03-e2f6cf27da1b@linux-instance:~/scripts$ cat changeJane.py
#!/usr/bin/env python3
import sys
import subprocess
f=open(sys.argv[1],"r")
#path='/home/<username>/data'
for line in f.readlines():
 old_name = line.strip()
 new_name = old_name.replace("jane", "jdoe")
 subprocess.run(["mv", old_name, new_name])
f.close()


student-03-e2f6cf27da1b@linux-instance:~/data$ if test -e ~/data/jane_profile_07272018.doc; then echo "File exists"; else echo "File doesn't exist"; fi
File exists

#We'll now use the redirection operator (>) to create an empty file simply by specifying the file name. The syntax for this is:
student-03-e2f6cf27da1b@linux-instance:~$ > test.txt
student-03-e2f6cf27da1b@linux-instance:~$ ls -l test.txt
-rw-r--r-- 1 student-03-e2f6cf27da1b student-03-e2f6cf27da1b 0 Feb  3 03:58 test.txt
student-03-e2f6cf27da1b@linux-instance:~$ echo "I am appending text to this test file" >> test.txt
student-03-e2f6cf27da1b@linux-instance:~$ cat test.txt
I am appending text to this test file

```









## Quiz

```python
#The check_web_address function checks if the text passed qualifies as a top-level web address, meaning that it contains alphanumeric characters (which includes letters, numbers, and underscores), as well as periods, dashes, and a plus sign, followed by a period and a character-only top-level domain such as ".com", ".info", ".edu", etc. Fill in the regular expression to do that, using escape characters, wildcards, repetition qualifiers, beginning and end-of-line characters, and character classes.
import re
def check_web_address(text):
  pattern = ___ #位置
  result = re.search(pattern, text)
  return result != None

print(check_web_address("gmail.com")) # True
print(check_web_address("www@google")) # False
print(check_web_address("www.Coursera.org")) # True
print(check_web_address("web-address.com/homepage")) # False
print(check_web_address("My_Favorite-Blog.US")) # True

A：  pattern = r"^[A-Za-z._-][^/@]*$"

#The check_time function checks for the time format of a 12-hour clock, as follows: the hour is between 1 and 12, with no leading zero, followed by a colon, then minutes between 00 and 59, then an optional space, and then AM or PM, in upper or lower case. Fill in the regular expression to do that. How many of the concepts that you just learned can you use here?
import re
def check_time(text):
  pattern = ___ #位置
  result = re.search(pattern, text, re.IGNORECASE)
  return result != None

print(check_time("12:45pm")) # True
print(check_time("9:59 AM")) # True
print(check_time("6:60am")) # False
print(check_time("five o'clock")) # False

A：  pattern = r"[1-12]*:[012345][0123456789][ ]?[AM|PM$]"
#The contains_acronym function checks the text for the presence of 2 or more characters or digits surrounded by parentheses, with at least the first character in uppercase (if it's a letter), returning True if the condition is met, or False otherwise. For example, "Instant messaging (IM) is a set of communication technologies used for text-based communication" should return True since (IM) satisfies the match conditions." Fill in the regular expression in this function:
import re
def contains_acronym(text):
    pattern = ____ #更改位置
    result = re.search(pattern, text)
    return result != None

print(contains_acronym("Instant messaging (IM) is a set of communication technologies used for text-based communication")) # True
print(contains_acronym("American Standard Code for Information Interchange (ASCII) is a character encoding standard for electronic communication")) # True
print(contains_acronym("Please do NOT enter without permission!")) # False
print(contains_acronym("PostScript is a fourth-generation programming language (4GL)")) # True
print(contains_acronym("Have fun using a self-contained underwater breathing apparatus (Scuba)!")) # True 

A：pattern = r"\([A-Z0-9][a-zA-Z0-9]*\)"
#Fill in the code to check if the text passed includes a possible U.S. zip code, formatted as follows: exactly 5 digits, and sometimes, but not always, followed by a dash with 4 more digits. The zip code needs to be preceded by at least one space, and cannot be at the start of the text.

import re
def check_zip_code (text):
  result = re.search(r"___", text) #位置
  return result != None
print(check_zip_code("The zip codes for New York are 10001 thru 11104.")) # True
print(check_zip_code("90210 is a TV show")) # False
print(check_zip_code("Their address is: 123 Main Street, Anytown, AZ 85258-0001.")) # True
print(check_zip_code("The Parliament of Canada is at 111 Wellington St, Ottawa, ON K1A0A9.")) # False

A：  result = re.search(r"[^0-9].*[ 0-9][0-9][0-9][0-9][0-9][0-9][-]?[0-9]?[0-9]?[0-9]?[0-9]?", text)
Or  result = re.search(r"[^0-9].*[ 0-9][0-9]{4}[-]?[0-9]?[0-9]?[0-9]?[0-9]?", text)
```

Practice Quiz: Advanced Regular Expressions

```python
# We're working with a CSV file, which contains employee information. Each record has a name field, followed by a phone number field, and a role field. The phone number field contains U.S. phone numbers, and needs to be modified to the international format, with "+1-" in front of the phone number. Fill in the regular expression, using groups, to use the transform_record function to do that.
import re
def transform_record(record):
  new_record = re.sub(___) #更改处
  return new_record

print(transform_record("Sabrina Green,802-867-5309,System Administrator")) 
# Sabrina Green,+1-802-867-5309,System Administrator

A:  new_record = re.sub(r",(?=\d)", r",+1-", record)
    
#The multi_vowel_words function returns all words with 3 or more consecutive vowels (a, e, i, o, u). Fill in the regular expression to do that.
import re
def multi_vowel_words(text):
  pattern = ___ #更改处
  result = re.findall(pattern, text)
  return result

print(multi_vowel_words("Life is beautiful")) 
# ['beautiful']
print(multi_vowel_words("Obviously, the queen is courageous and gracious.")) 
# ['Obviously', 'queen', 'courageous', 'gracious']

A:  pattern = r"\b\w*[aeiou]{3,}\w*\b"
#The transform_comments function converts comments in a Python script into those usable by a C compiler. This means looking for text that begins with a hash mark (#) and replacing it with double slashes (//), which is the C single-line comment indicator. For the purpose of this exercise, we'll ignore the possibility of a hash mark embedded inside of a Python command, and assume that it's only used to indicate a comment. We also want to treat repetitive hash marks (##), (###), etc., as a single comment indicator, to be replaced with just (//) and not (#//) or (//#). Fill in the parameters of the substitution method to complete this function: 
import re
def transform_comments(line_of_code):
  result = re.sub(___) #修改处
  return result
print(transform_comments("### Start of program")) 
# Should be "// Start of program"
print(transform_comments("  number = 0   ## Initialize the variable")) 
# Should be "  number = 0   // Initialize the variable"

A:  result = re.sub(r"[#]{1,}", r"//", line_of_code)
#The convert_phone_number function checks for a U.S. phone number format: XXX-XXX-XXXX (3 digits followed by a dash, 3 more digits followed by a dash, and 4 digits), and converts it to a more formal format that looks like this: (XXX) XXX-XXXX. Fill in the regular expression to complete this function.
import re
def convert_phone_number(phone):
  result = re.sub(___) #更改处
  return result
print(convert_phone_number("My number is 212-345-9999.")) # My number is (212) 345-9999.
print(convert_phone_number("Please call 888-555-1234")) # Please call (888) 555-1234

A:  result = re.sub(r"(\s)(\d{3})(-)", r" (\2) ", phone)
    
    

 #In this lab, we'll search for the CRON error that failed to start. To do this, we'll use a python script to search log files for a particular type of ERROR log. In this case, we'll search for a CRON error within the fishy.log file that failed to start by narrowing our search to "CRON ERROR Failed to start".   

[admin@c-8-client SelfLearning]$ cat fishy.log | head -6
July 31 00:06:21 mycomputername kernel[96041]: WARN Failed to start network connection
July 31 00:09:53 mycomputername updater[46711]: WARN Computer needs to be turned off and on again
July 31 00:12:36 mycomputername kernel[48462]: INFO Successfully connected
July 31 00:13:52 mycomputername updater[43530]: ERROR Error running Python2.exe: Segmentation Fault (core dumped)
July 31 00:16:13 mycomputername NetworkManager[63902]: WARN Failed to start application install
July 31 00:26:45 mycomputername CRON[83063]: INFO I'm sorry Dave. I'm afraid I can't do that

            
[root@c-8-client SelfLearning]# chmod 777 find_error.py
[root@c-8-client SelfLearning]# cat find_error.py
#!/usr/bin/env python3
import sys
import os
import re
def error_search(log_file):
  error = input("What is the error? ")
  returned_errors = []
  with open(log_file, mode='r',encoding='UTF-8') as file:
    for log in  file.readlines():
      error_patterns = ["error"]
      for i in range(len(error.split(' '))):
        error_patterns.append(r"{}".format(error.split(' ')[i].lower()))
      if all(re.search(error_pattern, log.lower()) for error_pattern in error_patterns):
        returned_errors.append(log)
    file.close()
  return returned_errors

def file_output(returned_errors):
  with open(os.path.expanduser('~') + '/errors_found.log', 'w') as file:
    for error in returned_errors:
      file.write(error)
    file.close()
if __name__ == "__main__":
  log_file = sys.argv[1]
  returned_errors = error_search(log_file)
  file_output(returned_errors)
  sys.exit(0)

[root@c-8-client SelfLearning]# ./find_error.py ./fishy.log
What is the error? CRON ERROR Failed to start
            
[root@c-8-client ~]# pwd
/root
[root@c-8-client ~]# cat errors_found.log
July 31 04:11:32 mycomputername CRON[51253]: ERROR: Failed to start CRON job due to script syntax error. Inform the CRON job owner!

               
                
                
                
```





## Final Challenge 

```bash
student-04-3976a731bf1b@linux-instance:~$ cat syslog.log
Jan 31 00:09:39 ubuntu.local ticky: INFO Created ticket [#4217] (mdouglas)
Jan 31 00:16:25 ubuntu.local ticky: INFO Closed ticket [#1754] (noel)
Jan 31 00:21:30 ubuntu.local ticky: ERROR The ticket was modified while updating (breee)
Jan 31 00:44:34 ubuntu.local ticky: ERROR Permission denied while closing ticket (ac)
Jan 31 01:00:50 ubuntu.local ticky: INFO Commented on ticket [#4709] (blossom)
Jan 31 01:29:16 ubuntu.local ticky: INFO Commented on ticket [#6518] (rr.robinson)
Jan 31 01:33:12 ubuntu.local ticky: ERROR Tried to add information to closed ticket (mcintosh)
Jan 31 01:43:10 ubuntu.local ticky: ERROR Tried to add information to closed ticket (jackowens)
Jan 31 03:05:35 ubuntu.local ticky: ERROR Timeout while retrieving information (ahmed.miller)
....下略
```

```bash
student-04-3976a731bf1b@linux-instance:~$ cat csv_to_html.py
#!/usr/bin/env python3
import sys
import csv
import os

def process_csv(csv_file):
    """Turn the contents of the CSV file into a list of lists"""
    print("Processing {}".format(csv_file))
    with open(csv_file,"r") as datafile:
        data = list(csv.reader(datafile))
    return data

def data_to_html(title, data):
    """Turns a list of lists into an HTML table"""

    # HTML Headers
    html_content = """
<html>
<head>
<style>
table {
  width: 25%;
  font-family: arial, sans-serif;
  border-collapse: collapse;
}

tr:nth-child(odd) {
  background-color: #dddddd;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}
</style>
</head>
<body>
"""


    # Add the header part with the given title
    html_content += "<h2>{}</h2><table>".format(title)

    # Add each row in data as a row in the table
    # The first line is special and gets treated separately
    for i, row in enumerate(data):
        html_content += "<tr>"
        for column in row:
            if i == 0:
                html_content += "<th>{}</th>".format(column)
            else:
                html_content += "<td>{}</td>".format(column)
        html_content += "</tr>"

    html_content += """</tr></table></body></html>"""
    return html_content


def write_html_file(html_string, html_file):

    # Making a note of whether the html file we're writing exists or not
    if os.path.exists(html_file):
        print("{} already exists. Overwriting...".format(html_file))

    with open(html_file,'w') as htmlfile:
        htmlfile.write(html_string)
    print("Table succesfully written to {}".format(html_file))

def main():
    """Verifies the arguments and then calls the processing function"""
    # Check that command-line arguments are included
    if len(sys.argv) < 3:
        print("ERROR: Missing command-line argument!")
        print("Exiting program...")
        sys.exit(1)

    # Open the files
    csv_file = sys.argv[1]
    html_file = sys.argv[2]

    # Check that file extensions are included
    if ".csv" not in csv_file:
        print('Missing ".csv" file extension from first command-line argument!')
        print("Exiting program...")
        sys.exit(1)

    if ".html" not in html_file:
        print('Missing ".html" file extension from second command-line argument!')
        print("Exiting program...")
        sys.exit(1)

    # Check that the csv file exists
    if not os.path.exists(csv_file):
        print("{} does not exist".format(csv_file))
        print("Exiting program...")
        sys.exit(1)

    # Process the data and turn it into an HTML
    data = process_csv(csv_file)
    title = os.path.splitext(os.path.basename(csv_file))[0].replace("_", " ").title()
    html_string = data_to_html(title, data)
    write_html_file(html_string, html_file)

if __name__ == "__main__":
    main()
```

* **Challenge**

```markdown
Here's your challenge: Write a script to generate two different reports based on the ranking of errors generated by the system and the user usage statistics for the service. You'll write the script on your own, but we'll guide you throughout.

First, import all the Python modules that you'll use in this Python script. After importing the necessary modules, initialize two dictionaries: one for the number of different error messages and another to count the number of entries for each user (splitting between INFO and ERROR).

Now, parse through each log entry in the syslog.log file by iterating over the file.

For each log entry, you'll have to first check if it matches the INFO or ERROR message formats. You should use regular expressions for this. When you get a successful match, add one to the corresponding value in the per_user dictionary. If you get an ERROR message, add one to the corresponding entry in the error dictionary by using proper data structure.

After you've processed the log entries from the syslog.log file, you need to sort both the per_user and error dictionary before creating CSV report files.

Keep in mind that:

* The error dictionary should be sorted by the number of errors from most common to least common.
* The user dictionary should be sorted by username.

Insert column names as ("Error", "Count") at the zero index position of the sorted error dictionary. And insert column names as ("Username", "INFO", "ERROR") at the zero index position of the sorted per_user dictionary.

After sorting these dictionaries, store them in two different files: **error_message.csv and user_statistics.csv**.

Save the ticky_check.py file by clicking Ctrl-o, Enter key, and Ctrl-x.
```

* **Take the Challenge**

```python
student-04-3976a731bf1b@linux-instance:~$ cat ./ticky_check.py
#!/usr/bin/env python3

import os
import re
import sys
import operator
import csv

error_counter = {}
error_user = {}
info_user = {}

#This function will read each line of the syslog.log file and check if it is an error or an info message.
def search_file():
    with open('syslog.log', "r") as myfile:
     for line in myfile:
        if " ERROR " in line:
            find_error(line)
            add_user_list(line, 1)
        elif " INFO " in line:
            add_user_list(line, 2)
    return


#If it is an error it will read the error from the line and increment into the dictionary
def find_error(str):
    match = re.search(r"(ERROR [\w \[]*) ", str)
    if match is not None:
        aux = match.group(0).replace("ERROR ", "").strip()
        if aux == "Ticket":
         aux = "Ticket doesn't exist"
        if not aux in error_counter:
            error_counter[aux] = 1
        else:
            error_counter[aux] += 1
    return

#This whill read the user from the string and add to the error or the info counter depending on the op number
def add_user_list(str, op):
    match = re.search(r'\(.*?\)', str)
    user = match.group(0)
    userA = user.strip("()")
    if op == 1:
        if not userA in error_user:
            error_user[userA] = 1
        else:
            error_user[userA] += 1
    elif op == 2:
        if not userA in info_user:
            info_user[userA] = 1
        else:
            info_user[userA] += 1
    return

#This function will read the list, arrange it and return a tuple with the dictionary items
def sort_list(op, list):
    if op == 1:
        s = sorted(list.items(), key=operator.itemgetter(1), reverse=True)
    elif op == 2:
        s = sorted(list.items(), key=operator.itemgetter(0))
    return s

#This is an extra function which will read the value of a user in the error dictionary and return its value if key exists
def getErrValue(keyV):
    for key, value in error_user:
        if key is keyV:
            return value
    return 0

#This function writes both csv files
def write_csv(op):
    if op == 1:
        with open('user_statistics.csv', 'w', newline='') as output:
            fieldnames = ['Username', 'INFO', 'ERROR']
            csvw = csv.DictWriter(output, fieldnames=fieldnames)
            csvw.writeheader()
            for key, value in info_user:
                valError = getErrValue(key)
                csvw.writerow({'Username': key, 'INFO': value, 'ERROR': valError})
    if op == 2:
        with open('error_message.csv', 'w', newline='') as output:
            fieldnames = ['Error', 'Count']
            csvw = csv.DictWriter(output, fieldnames=fieldnames)
            csvw.writeheader()
            for key, value in error_counter:
                csvw.writerow({'Error': key, 'Count': value})
    return

#This function adds zero to the other dictionary in case that user is not a key, it will add a key with the user and value 0
def add_zeros():
    for user in error_user.keys():
        if user not in info_user:
            info_user[user] = 0
    for user in info_user.keys():
        if user not in error_user:
            error_user[user] = 0
    return


#This will execute the functions
search_file()
add_zeros()
error_counter = sort_list(1, error_counter)
error_user = sort_list(2, error_user)
info_user = sort_list(2, info_user)
write_csv(1)
write_csv(2)
student-04-3976a731bf1b@linux-instance:~$
```

* **The Result**

```bash
student-04-3976a731bf1b@linux-instance:~$ sudo chmod +x ticky_check.py
student-04-3976a731bf1b@linux-instance:~$ ./ticky_check.py
student-04-3976a731bf1b@linux-instance:~$ ./csv_to_html.py error_message.csv /var/www/html/Error.html
Processing error_message.csv
Table succesfully written to /var/www/html/Error.html
student-04-3976a731bf1b@linux-instance:~$ ./csv_to_html.py user_statistics.csv /var/www/html/User.html
Processing user_statistics.csv

student-04-3976a731bf1b@linux-instance:~$ ls /var/www/html/
Error.html  index.nginx-debian.html  test_file0208.html  User.html

student-04-3976a731bf1b@linux-instance:~$ cat error_message.csv
Error,Count
Timeout while retrieving information,15
Connection to DB failed,13
Tried to add information to closed ticket,12
Permission denied while closing ticket,10
The ticket was modified while updating,9
Ticket doesn't exist,7
student-04-3976a731bf1b@linux-instance:~$ cat user_statistics.csv
Username,INFO,ERROR
ac,2,0
ahmed.miller,2,0
blossom,2,0
bpacheco,0,2
breee,1,0
britanni,1,0
enim.non,2,0
flavia,0,5
jackowens,2,0
kirknixon,2,0
mai.hendrix,0,3
mcintosh,4,0
mdouglas,2,0
montanap,0,4
noel,6,0
nonummy,2,0
oren,2,0
rr.robinson,2,0
sri,2,0
xlg,0,4

#Open the browser and check the html file. Replace the IP address accordingly.
http://35.192.18.134/User.html
http://35.192.18.134/Error.html
```




















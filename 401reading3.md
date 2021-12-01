# 401 Reading 3 FileIO & Exceptions

## Read & Write Files in Python 
[Reading](https://realpython.com/read-write-files-python/)
Files consist of a Header, Data, and EOF. Header stores metadata about the contents, data is the contents, and EOF is a special character that indicates the end of the file.

File Paths are made of a string telling where the file is. It contains the Folder Path, File Name, and Extension (.py for example)

To close open a file in Python you can use the open('filename') method. To close it you can either use a try: finally: block or a with statement on the open method.

You can also use a positinal arugtment called mode. Example given:
```
with open('dog_breeds.txt', 'r') as reader:
    # Further file processing goes here
```

Character	Meaning
'r'	Open for reading (default)
'w'	Open for writing, truncating (overwriting) the file first
'rb' or 'wb'	Open in binary mode (read/write using byte data)

There are three different categories of file objects:

Text files
Buffered binary files
Raw binary files

Example for iterating over to read:
```
>>> with open('dog_breeds.txt', 'r') as reader:
>>>     # Read and print the entire file line by line
>>>     for line in reader:
>>>         print(line, end='')
```

Example of switching from \r\n endings to \n
```
"""
A simple script and library to convert files or strings from dos like
line endings with Unix like line endings.
"""

import argparse
import os


def str2unix(input_str: str) -> str:
    r"""
    Converts the string from \r\n line endings to \n

    Parameters
    ----------
    input_str
        The string whose line endings will be converted

    Returns
    -------
        The converted string
    """
    r_str = input_str.replace('\r\n', '\n')
    return r_str


def dos2unix(source_file: str, dest_file: str):
    """
    Converts a file that contains Dos like line endings into Unix like

    Parameters
    ----------
    source_file
        The path to the source file to be converted
    dest_file
        The path to the converted file for output
    """
    # NOTE: Could add file existence checking and file overwriting
    # protection
    with open(source_file, 'r') as reader:
        dos_content = reader.read()

    unix_content = str2unix(dos_content)

    with open(dest_file, 'w') as writer:
        writer.write(unix_content)


if __name__ == "__main__":
    # Create our Argument parser and set its description
    parser = argparse.ArgumentParser(
        description="Script that converts a DOS like file to an Unix like file",
    )

    # Add the arguments:
    #   - source_file: the source file we want to convert
    #   - dest_file: the destination where the output should go

    # Note: the use of the argument type of argparse.FileType could
    # streamline some things
    parser.add_argument(
        'source_file',
        help='The location of the source '
    )

    parser.add_argument(
        '--dest_file',
        help='Location of dest file (default: source_file appended with `_unix`',
        default=None
    )

    # Parse the args (argparse automatically grabs the values from
    # sys.argv)
    args = parser.parse_args()

    s_file = args.source_file
    d_file = args.dest_file

    # If the destination file wasn't passed, then assume we want to
    # create a new file based on the old one
    if d_file is None:
        file_path, file_extension = os.path.splitext(s_file)
        d_file = f'{file_path}_unix{file_extension}'

    dos2unix(s_file, d_file)
```
To append to a file use the mode argument of a.
```
with open('dog_breeds.txt', 'a') as a_writer:
    a_writer.write('\nBeagle')
```

You can also read one file while writing in another:
```
d_path = 'dog_breeds.txt'
d_r_path = 'dog_breeds_reversed.txt'
with open(d_path, 'r') as reader, open(d_r_path, 'w') as writer:
    dog_breeds = reader.readlines()
    writer.writelines(reversed(dog_breeds))
```


## Exceptions in Python
[Exceptions Reading](https://realpython.com/python-exceptions/)

You can use "raise Exception" when a certain condition occurs to throw an error.

You can also assert something happens. 
Ex
```
import sys
assert ('linux' in sys.platform), "This code runs on Linux only."
```

A try clause is executed up until the point where the first exception is encountered.
Inside the except clause, or the exception handler, you determine how the program responds to the exception.
You can anticipate multiple exceptions and differentiate how the program should respond to them.

Summary given from reading:
raise allows you to throw an exception at any time.
assert enables you to verify if a certain condition is met and throw an exception if it isn’t.
In the try clause, all statements are executed until an exception is encountered.
except is used to catch and handle the exception(s) that are encountered in the try clause.
else lets you code sections that should run only when no exceptions are encountered in the try clause.
finally enables you to execute sections of code that should always run, with or without any previously encountered exceptions.

[Back](README.md)
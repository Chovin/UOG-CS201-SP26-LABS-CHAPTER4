# Lab 4: File Input and Output

These series of labs will cover some ways of reading from and writing to files in Python as well as string manipulation using a variety of string methods. 

The goal is to learn how to manipulate strings, store data, process information, and generate output files. 

Below is a summary of what was covered in chapter 4.

#### Some File Operations in Python

Function/Method | Description | Example Usage | Docs 
---|---|---|---
`open(filename, mode='r')` | Opens a file and returns a file object. | `file = open('data.txt')` <br><br> `file = open('data.txt', 'w')` | <u>[📚](https://docs.python.org/3/builtins/functions.html#open)</u>
`.read()` | Reads the entire contents of a file as a string. | `content = file.read()` | <u>[📚](https://docs.python.org/3/library/io.html#io.TextIOBase.read)</u>
`.readline()` | Reads one line from the file at a time. | `line = file.readline()` | <u>[📚](https://docs.python.org/3/library/io.html#io.TextIOBase.readline)</u>
`.readlines()` | Reads all lines into a list, each item being a string of that line (with the separating `\n` at the end). | `lines = file.readlines()` | <u>[📚](https://docs.python.org/3/library/io.html#io.IOBase.readlines)</u>
`.write(string)` | Writes a string to the file. | `file.write("Hello, World!")` | <u>[📚](https://docs.python.org/3/library/io.html#io.Writer.write)</u>
`.close()` | Closing files once you're done is important. Doing so frees up system resources, avoids corruption, and allows other programs to access the file. | `file.close()` | <u>[📚](https://docs.python.org/3/library/io.html#io.IOBase.close)</u>

##### Best Practice

<table>
    <tr>
        <th>
            Syntax
        </th>
        <th>
            Description
        </th>
        <th>
            Example Usage
        </th>
        <th>
            Docs
        </th>
    </tr>
    <tr>
        <td>

```py
with <EXPRESSION> [as <VARIABLE>]:
    <CODE_BLOCK>
```
  
</td> <!-- fun. looks like the markdown renderer needs there to be no indents before this because of the code block --> 
        <td>
            Using a context manager (the <code>with</code> keyword) automatically closes the file once you're done with it, so you don't need to manually use the <code>.close()</code> method.
        </td>
        <td>

```py
with open('file.txt', 'r') as f:
    stuff = f.read()
    print(stuff)
# once execution reaches here, the file is closed
```

</td>
        <td>
            <u>

[📚](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files:~:text=It%20is%20good%20practice,try%2Dfinally%20blocks%3A)

</u>
        </td>
    </tr>
</table>

#### Common File Modes

Mode | Description
---|---
`'r'` | **Read** - Default value. Opens a file for reading, error if the file does not exist.
`'w'` | **Write** - Opens a file for writing, creates the file if it does not exist. **This will overwrite the existing content.**
`'a'` | **Append** - Opens a file for appending, creates the file if it does not exist. New data is added to the end.
`'r+'` | **Read/Write** - Opens a file for both reading and writing.


#### Useful String Methods for File Processing

When working with text from files, you will frequently need to clean, split, or analyze strings. Here are some essential string methods to master. You can read more about them and other string methods in the [docs 📚](https://docs.python.org/3/builtins/stdtypes.html#string-methods).

Method | Description | Example | Result
---|---|---|---
`.strip(chars=None)` | Removes leading and trailing characters (whitespace by default). | `"  hello world\n".strip()` <br><br> `"Hello World!".strip("!")` | `"hello world"` <br><br> `"Hello World"`
`.split(sep=None)` | Splits a string into a list of substrings based on whitespace by default. Be wary of change in behavior when specifying `sep` vs. not. You can read more in the [docs](https://docs.python.org/3/builtins/stdtypes.html#str.split). | `"Na Na Na\nBatman".split()` <br><br> `"apple,banana,grape".split(',')` | `['Na', 'Na', 'Na', 'Batman']` <br><br> `['apple', 'banana', 'grape']`
`.join(iterable)` | Joins elements of a list into a single string using a specified separator. | `"-".join(['2024', '03', '11'])` | `"2024-03-11"`
`.replace(old, new)` | Replaces occurrences of a substring with another substring. | `"Omg, a cat! I love cats".replace("cat", "dog")` | `'Omg, a dog! I love dogs'`
`.lower()` | Converts all characters in the string to lowercase. | `"Hello World".lower()` | `"hello world"`
`.upper()` | Converts all characters in the string to uppercase. | `"Hello World".upper()` | `"HELLO WORLD"`
`.startswith(prefix)` | Checks if the string starts with the specified prefix. | `"report.txt".startswith("report")` | `True`
`.endswith(suffix)` | Checks if the string ends with the specified suffix. | `"report.txt".endswith(".txt")` | `True`
`.find(sub)` | Returns the lowest index where the substring is found, or `-1` if not found. | `"hello world".find("world")` | `6`
`.count(sub)` | Returns the number of non-overlapping occurences of `sub` in the string. | `"she sells sea shells by the sea shore".count("sh")` <br><br> `"wallet".count("dollar")` | `3` <br><br> `0`
`.isalpha()` / `.isdigit()` | Checks if all characters in the string are alphabetic / digits. | `"123".isdigit()` / `"abc".isalpha()` | `True` / `True`

##### Best Practice

Syntax | Description | Example | Result
---|---|---|---
`<item or substring> in <collection or string>` | `.find()` gives you the index of the substring, but if you don't care about the index and only want to know if a substring is contained within another string, it's best to use the `in` operator because it is more efficient, more readable, and less prone to logic errors. | `"i" in "team"` | `False`

#### Other String Manipulation

You can use the slicing operator on any sequence (strings are also sequences 🙂) to return a new sequence (like a string! 👀) that is built by accessing certain elements in a certain order specified by the operands given. Negative integers can be given for all these operands and they will be counted from the back of the sequence (`-1` being the last item) or step backwards

Syntax | Description | Example | Result
---|---|---|---
`<str>[index]` | Returns the character at the given `index` | `"I love butter"[4]` <br><br> `"I love butter"[-1]` | `'v'` <br><br> `'r'`
`<str>[start:stop]` | Returns the substring in the interval **[start, stop)**. In other words, from `start` inclusive to `stop` exclusive. Both `start` and `stop` can be omitted to represent the rest of the string from the beginning or end. | ` "I love butter"[7:11]` <br><br> `"I love butter"[:11]` <br><br> `"I love butter"[-6:]` | `'butt'` <br><br> `'I love butt'` <br><br> `'butter'
`
`<str>[start:stop:step]` | Returns the substring in the interval **[start, stop)** with a step size of `step` (defaults to `1`) | `"0123456789"[::2]` <br><br> `"I love butter"[2:-1:2]` <br><br> `"I love butter"[2:-2:2]` <br><br> `"I love butter"[::-1]` | `'02468'` <br><br> `'lv ut'` <br><br> `'lv ut'` <br><br> `'rettub evol I'`

#### Other Useful Functions

Function | Description | Example | Result
---|---|---|---
`chr(integer)` | Returns the Unicode (extension of ASCII) character represented by the `integer` given | `chr(65)` <br><br> `chr(129505)` | `'A'` <br><br> `'🧡'`
`ord(character)` | Returns the Unicode (extension of ASCII) number assigned to the given `character`. This is the inverse of `chr()` | `ord('A')` <br><br> `ord('🧡'))` | `65` <br><br> `129505`


## Grading Criteria

Like the previous labs, I will grade for functionality, but documentation will also be key components of your grade. Good documentation helps explain your logic, especially when processing data.

Lab | Description | Comments/Documentation | Functionality | Total
---|---|---|---|---
Lab4a | Palindrome | 5pts | 5pts | 10pts
Lab4b | Decimal to Hexademical  | 4pts | 6pts | 10pts
Lab4c | Emotional to Decimal | 4pts | 6pts | 10pts
Lab4d | Clean lyrics! | 10pts | 10pts | 20pts
Lab4e | The grade reporter | 10pts | 15pts | 25pts
Lab4f | D̵̖͂E̶̯͂̈́Ć̶̼͔̎Ò̵͉͆D̶͒̅͜͜Ë̷͈̟́ ̵̯̙̆͒T̶̛͈̉H̴̭̎E̵̥̞̍̕ ̴̢̈͜V̶̫͈̈O̶͕͋̔I̵̪͝͝ͅD̵̖͑ ̴̣̤̅—̴̥̮̆͆ ̵̬͑̔O̷̦͓̿P̵̧̙̑Ę̷͗͜R̵̨͓͝A̷̠͝͝Ṫ̶̳̦Î̵̠͔Ò̷̩̤͑N̶͚̝̽̕:̴͍̱̓̅ ̸̹̔M̸͚͒A̷̦͛Ṋ̷̾̄ ̶͚̳͌͋Ȉ̴̫̭N̵̮̥̋̒ ̴͍͚͒Ť̴̡̯̎Ḥ̴̛͛Ę̸̖̽ ̷̟̽M̷̧͌̅Í̸̡̬̊D̷̘̩̈̉D̸͉̍L̷̻̒̏Ȩ̴̗́| 10pts | 15 pts | 25pts
Total | | | | **100pts**
# General Instructions

Like always, each Lab should have the following header:
```
"""
Author: Your Name
Date: Today's Date/Due Date
FileName: The File's Name
Purpose: What the program is about
"""
```

For your file names, please name each lab by the following `<specificlabname>_<yourlastname><firstnameinitials>.py`

So for example, If I am turning in Lab 4e, the file name would be `clean_lyrics_galangmi.py`

These challenges are solvable with what you already know. There are hints\* given for each in collapsable sections that look like this:

<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> ### here's some review!
> blah blah blah

</details>

\* programming trains you to deconstruct complex problems into logical steps, invent creative solutions from scratch, and view failures as data points to adapt to change. Those are the skills you really want to learn. If you rely on the hints without spending time and effort trying to solve the problem yourself however, you will learn less of those skills which will make your future programming endeavors, classes, and tests more difficult for you. For example, the last challenge in Lab 4 has been very difficult for past students. If you practice doing the challenges up until that one without using the hints, you will more likely have an eaasier time solving that challenge.. (hopefully!)

## Lab 4a: Palindromes
A palindrome is a word, phrase, or sequence that reads the same forwards and backwards (ignoring spaces, punctuation, and capitalization). Examples: "racecar", "madam", "taco cat", "A man, a plan, a canal: Panama!"

Create a program called `palindrome_checker.py` that asks the user for a word or phrase and determines if it's a palindrome.

The program should work with:
- Simple words
- Case-sensitive words ("racecar", "RACECAR", "RaCECar" should be treated the same)
- (Extra credit) Phrases (so it ignores punctuations like .,?,!,;,etc.)

Here are some test cases for you to work with:
- racecar
- madam
- kayak
- Bob

Extra credit (5pts): Have the program also work for strings with punctuation and whitespace.
- Taco Cat
- A man, a plan, a canal: Panama!


<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> ### There a many ways to do this. 
> Thinking about how you can use one or more of the following functions may help: `lower()`, `replace()`, `strip()`, `reversed()`, `split()`, `join()`, `for` or `while`

</details>

---

## Lab 4b and 4c: Number System Base Conversion (Radix Conversion)

We talked about how we use different number systems for different purposes. Decimal for every day human usage, binary for computers, hexidecimal for representing colors. In these challenges, we will be exploring changing between given bases.

Do you remember how to convert from decimal to hex?

<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> ### Lets understand how hex works:
> 
> **The Digits**: Hexadecimal uses 16 digits:
> - 0 - 9 represents values 0 to 9
> - A - F represents values 10 - 15
> 
> For example, lets take the decimal number 3410. Like in binary and octal, to convert this to hexadecimal, we divide by the base we are converting to (16 for hex). Keep track of the remainder as this is our hexadecimal bit, then use the quotient to continue dividing. Keep repeating this until our quotient is zero:
> 
> | Step | Division | Quotient | Remainder | Remainder in Hex |
> |:----:|:--------:|:--------:|:---------:|:----------------:|
> | 1 | 3410 ÷ 16 | 213 | 2 | 2 |
> | 2 | 213 ÷ 16 | 13 | 5 | 5 |
> | 3 | 13 ÷ 16 | 0 | 13 | D |
> 
> **Note:** Read the remainders from **bottom to top**: D 5 2

</details>

How about converting back from hex to decimal?

<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> To convert back, just like decimal has ones place ($10^0$), tens place ($10^1$), hundreds place ($10^2$), hex has places that are powers of 16. each bit is multiplied by a power of 16, and added together.
> 
> So for example: `D52`
> 
> $$ 2 \times 16^0 = 2 \\ 5 \times 16^1 = 80 \\ D \times 16^2 = 13 * 256 = 3328 $$
> 
> Thus `D52 = 2 + 80 + 3328 = 3410`

</details>

### Lab4b

Create a program `decimal_to_hexadecimal.py` that converts decimal to hexadecimal. This will be your **Lab 4B**.

Just note that it is much easier to have the output (hexadecimal) be in a string since we have to convert values remainders 10-15 to A-F. 

<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> ***Some Useful Tools***
> 
> | Category | Functions/Operations | Purpose |
> |:---------|:---------------------|:--------|
> | **Math Operations** | `//` (integer division) | Get quotient |
> | | `%` (modulo) | Get remainder |
> | | `while` loop | Repeat division until quotient is 0 |
> | **String Building** | String concatenation (`+`) | Build hex string from remainders |
> | | `str()` | Convert numbers to strings |
> | | `""` (empty string) | Start with empty string |
> | **Digit Conversion** | `if/elif/else` | Convert 10-15 to A-F |
> | | `0-9` digits | Keep as-is |
> | | `10-15` | Map to 'A' through 'F' |

</details>

### Lab 4c

Our base can be whatever number we want though, and so can the symbols we use as our digits. We don't have to start with the numbers we know and love. 

For **Lab 4c**, we will be using a number system with base 3 and for the digits, we will be using these emojis: 

😭😐🥰

form left to right, they represent **none** (😭) to the **maximum value** (🥰) that can be represented by one digit in this number system.

We will call this number system "emotional".

Create a program `emotional_to_decimal.py` that converts emotional to decimal.

<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> ***Things to think about***
> 
> * What number represents "none"?
> * What would be the maximum number representable by a digit in base 3? 
> * What about in base 2?
> * If you write out what the number would be using regular numbers as digits, does that make it easier to understand? can you work backwards from there?
> 
> ***Some Useful Tools***
> 
> | Category | Functions/Operations | Purpose |
> |:---------|:---------------------|:--------|
> | **String Processing** | `len()` | Get length of hex string |
> | | String indexing `a[i]` | Access each digit |
> | | `.upper()` | Convert to uppercase for consistent processing |
> | | `for` loop | Iterate through each digit |
> | **Digit Conversion** | `if/elif/else` | Convert eomtions to numbers |
> | **Math Operations** | `**` (exponentiation) | Calculate powers of 16 |
> | | `*` (multiplication) | Multiply digit by place value |
> | | `+` (addition) | Accumulate total |

</details>

---

## Lab 4d: Clean lyrics!
Radio stations that play music really hates curse words, profanity, and very explicit lyrics. So they would usually blur curse words like sh\*t, b\*tch, and many more! 

**The rules for cleaning:**
- Replace each character in the curse word with * (e.g., "shit" becomes "****")
- Keep the first letter visible (e.g., "shit" becomes "s***")
- Or use a standard bleep sound: "[BLEEP]". You decide which rule to implement!

List of curse words (considered for this lab): "sh\*t", "b\*tch", "f\*ck". You may expand the list if you wish, just note that in your docstring. 

Create a program called `clean_lyrics.py` that reads any song lyrics from a text file and creates a "clean" version suitable for radio broadcast. 
The program should do the following:
- Output the clean version into a textfile called `songname_clean.txt`.
- Check for sensitive cases, "Shit", "SHIT", "shit", etc. should be treated the same. 
- Also, please note that some music artists may express profanity differently, so things like "b\*tchin", "b\*tchy", "f\*cker", "f\*cked", etc. I don't expect you to get through all cases, but try your best to account for cases like these.

You have some textfiles of song lyrics that you can test on: `rap_god.txt`, `snooze.txt`

<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> ***Some general tips***
> - You can create your list of curse words and check if a word is in that list.
> - Remember, you can iterate through a line by converting a line into a list 
> - Alternatevely, you can use the `replace()` function for strings (however, this is much trickier)
> - You can nest a read and write function
> - You can account for different 
> 
> Some functions/operations that may serve useful: `open()`, `readlines()`, `split()`, `lower> ()`, `replace()`

</details>

---

## Lab 4e: The grade reporter

Lets modify Lab 3b and turn it to an auto grader! You are given a `grades.txt` (that was generated randomly). The structure is the following format:
```
StudentName,TestAverage,QuizAverage,AssignmentAverage,ProjectAverage,FinalExamScore
```

For example:
```
Maria Santos,94.3,100,103.2,97.7,89.3
Jose Cruz,82.3,100,91.4,87.0,75.5
Ana Leon-Guerrero,78.5,92.5,88.0,91.2,82.8
```

Your job is to create a program called `grade_reporter.py` that reads the textfile, calculates each student's final grade and letter grade (using the same grade scale from lab3b) and saves the results into a new text file called `graded.txt`.

<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> Some pointers: 
> 
> - Please view the text file and understand how you can grab the contents and plug those numbers into your lab 3b to get a letter grade. Maybe you can split them into a list and read the numbers?
> 
> - You also need to think on how you can write these as well
> 
> Possibly Helpful Functions/Operations: `open(filename, 'r')`, `open(filename, 'w')`, `readlines()` or `for line in file`, `strip()` to remove the newline (`\n`), `float()`, `split(',')`. 
> 
> You also need understanding of indexing.

</details>

---

## L̴̦̐̅a̵̢͘b̵̯̎̐ ̸͇͌4̵̙̓ḟ̵̳̩̃:̶̅͘ͅ ̷̨̜̈́̚D̵̖͂E̶̯͂̈́Ć̶̼͔̎Ò̵͉͆D̶͒̅͜͜Ë̷͈̟́ ̵̯̙̆͒T̶̛͈̉H̴̭̎E̵̥̞̍̕ ̴̢̈͜V̶̫͈̈O̶͕͋̔I̵̪͝͝ͅD̵̖͑ ̴̣̤̅—̴̥̮̆͆ ̵̬͑̔O̷̦͓̿P̵̧̙̑Ę̷͗͜R̵̨͓͝A̷̠͝͝Ṫ̶̳̦Î̵̠͔Ò̷̩̤͑N̶͚̝̽̕:̴͍̱̓̅ ̸̹̔M̸͚͒A̷̦͛Ṋ̷̾̄ ̶͚̳͌͋Ȉ̴̫̭N̵̮̥̋̒ ̴͍͚͒Ť̴̡̯̎Ḥ̴̛͛Ę̸̖̽ ̷̟̽M̷̧͌̅Í̸̡̬̊D̷̘̩̈̉D̸͉̍L̷̻̒̏Ȩ̴̗́

***TOP SECRET // CLASSIFIED // EYES ONLY***

---

### D̴O̷S̸S̶I̴E̷R̷:̸ ̸O̵P̷E̵R̷A̶T̵I̷O̴N̴ ̷V̵O̸I̷D̷

To: Special Agent [YOUR NAME], FBI Cyber Crimes Task Force

From: Assistand Director, MarkIrahCarey

Subject: URGENT - Immediate Action Required

Special Agent [YOUR NAME],

For the past six months, you've been tracking a cybercriminal organization known as "The Void". They are a known group responsible for stealing over $1.76 billion from banks across the country. They've hit institutions in New York, Chicago, and Los Angeles.

They are ghosts. Until now.

#### THE INTEL (Let's just say... acquired through "̷̱̣̖̦͋̚a̶͈͗l̸͉͆̿͂̂t̵̛͓̪̣͚̾̚e̸̖̬͚͉̾̀̾̚r̶͙̀̓n̵͈͎̆͆̄̋ã̵̮̼̏̋ͅt̴̃ͅí̷̪̠͋̉̇v̶̟̦̾̎̚͜ȇ̵̘̤̞͛ ̷͉̠̫́̓̓m̸̰̀̓e̵̗̣̎̽͒̀ͅą̶͎̠͌̈́n̶̯̝͘s̴͖͇̲̈̈"̸̙̱̱͂̀)

Three days ago, a very good friend of mine, lets say... a *confidential informant*, had ties to the underground scene passed us a encrypted drive. They told me it contained some information that *could* be useful. 

The drive had **47 locked files**. Each one protected with its own password. Took my team six days to crack through all the files, but we finally got in. Nothing earth-shattering at first glance. Just small talk. Gah! Felt like we wasted a week on nothing.

But we decided to go through the files one more time. Then it hit us. One detail stood out, **LOG #VOID-035**:

> ...the big meeting between Ghost and Wraith happens soon. they only communicate directly when something massive is planned. last time they talked, three banks fell. It is rumored that **Guam is next...**"

Guam.

That changes everything.

My team worked double time. Our goal was to incercept this conversation! We tapped on a compromised router believed to be used by Void operatives thanks to our *confidential informant*. If they were planning something in our backyard, we needed to know exactly when and where.

Then, last night at 02:10 AM, we got lucky.

We had monitored for a couple days and had thought it was a dud, a fake to throw us off. But, at 02:13 AM, traffic appeared. Two IP addresses we've been watching for months suddenly lit up.

**Ghost and Wraith were talking.**

The tap was running for a bit, long enough to capture their conversation. But then they noticed something. The connection cut out. Our attack was compromised!

It's fine though. We managed to record everything before they kicked us out.

But here's the problem: it's encrypted with their **custom cipher**. Our cryptographers say it could take weeks to crack.

We don't have weeks.

Guam doesn't have weeks.

That's where you come in, Agent [YOUR NAME].

**Your job:** Decode their conversation and figure out what they're planning.

A colleague of yours has the decrptyed log files. 

Please... save Guam.

---
### THE CASE FILES

Thanks to Assistant Director MarkIrahCarey and your months of investigation, you flip through notes and find scattered pieces of intelligence. Most of the log files are just duds, but you found some very useful information:

#### EVIDENCE LOG #VOID-25
Source: Decrypted Drive

```
...can't use standard Caesar, too obvious...
...we need something they won't expect...
...if A becomes B, too simple...
...what if we reverse the alphabet? A=Z, B=Y, C=X...
...call it the "mirror cipher"...
...test: "hello" becomes "svool"...
...Ghost likes it. Wraith says too confusing but Ghost insists...
...fine, we use it for all sensitive comms...
```

#### EVIDENCE LOG #VOID-47
Source: Decrypted Drive

```
...did you see Ghost's message yesterday? He used the mirror again...
...Wraith still hates it but it works...
...remember: the mirror doesn't change spaces or punctuation...
...only letters A-Z...
...but agh! its also case-insensitive! maybe I am too dumb. How the hell do we read this anyway...
```

#### EVIDENCE WRITTEN NOTE
The note is partically encrypted, but we have recovered some information
```
Mirror key:

A B C D̷̤̜̎́̾ ̷̧̭͚̂͗Ë̷̙̱͎́̇̈́̕͝ ̴̳̥͎̭̄F̶̪̱̥̬̥͒̽̐ ̷̡̻̻̫̓̓G̸̜̟̯̣̏̊͂͗͝ ̷̲̳̯̬́Ḧ̷́͆̌͜ ̴̝͐̕͝Ị̶͙̯͎̌̀̾̓͝ ̷̟̓̒̇J̶̯͓̱̇̆̿̋͜͜ ̴̗͚̓͒̃K̵̟̉̾͜ ̸̡̥̣̺̝̾̏̌͊L̷͖̙̣̖͌̈́̍̀ ̷̢͕̝͆̐M̵̺͖͇̿
|̵̡̬̬͖͌ ̴̺͕̆̓̈́|̴̺̰̊ ̴̞̖͇̺̂͆̓͐́|̴̮͉̍̄ ̴̢̮̟͊|̴̟̘̄͊ ̸̡̥͕͉͗͛̄|̴̰̞̫͒́̏̋ ̶̳̫͕̐̌̾͛͠|̷̣̝͈̮̘͛̈́͌ ̴̧̪͆|̵̝͖̻̝̉́͌ ̸͇̿͜͝|̸̧̠͊̇̃͂͘ ̵̨͎̰͗̈́̏|̶̧̝̀͆͂ ̸̛̪̻͈̞̎͠|̸̦͔̮̟̞̄͐͆͊͝ ̸͍̠͓͖̝͂|̵͙̖̇̌͌̏
Z Y X Ẃ̶̧͔̞͊̅͂͑ ̴̤̭̤̝̌͂̇̚V̸̧̪͓̞̹̿́̀̃̊ ̴̰͇̪͙̈͐Ȗ̴̖̞̪͆̈́ͅ ̸̨͈̖̀́̇̾ͅͅT̵͕̓͋͝ ̶͎̘̰͗̊́ͅS̸̢̧͖̳̝̃̉͗͠ ̶̦̜̀R̷̩̠̾͌ ̷̤̋Q̶̹̦͔̱̲̂̿ ̴̤̟͎̩͑͗̀̕͝P̴̥̫̬̋̈͆̈̀ ̸͎̀͛Ô̴̖̆̄̔̓ ̴̰͔̥̍́̊̍̚N̴̘̄̂̐͗̈

S̶̡͎̥̑̉ơ̸͉̅͑̈́:̵͎̋̈́
̸͎͔͛̉̈́̔͝
̵͕͙͉̈́̒̎͝H̷̡͍͉̱̻̅Ě̷̪̗̪̗̂̌͌L̸̯̽̑́̊̐L̵̪̭̋̏̅Ọ̶̞̑͋ ̵͍̘̣̗̭̇͝→̶̡͕̝̼͛̈́ ̷̣̗̺͈̇̂S̶̡͛͆̈́͒̀V̸̧͉̋̚͜O̵̰̊́͛͠Ơ̷̢̜̞̟̘Ļ̵̤̬̓͆͌
̶̮̐͘
̶͔͙́̃͐͘͘G̴̞̣̳̹̔͋͒̽͂H̷̡̟͒͊̆́̅Ó̷̮͊̓͝S̶͔̭̼͑͛̇̕T̶̺̠͒́͂̊̉ ̵̨͈͉̏→̵̙̻̟̉͗̀̇̿ ̸̜̂̇?̸̧͕̪̖͋̎͠?̷̙͚̠͉̯̅̽?̸̧͖͔̿͆̑̆͜?̸̨̬̫̫̉
```

#### EVIDENCE PHONE CALL
Source: Month 3, a deciphered phone call between two of Void and Wraith's lackeys (transcript)

```
Unknown Voice 1: "So remind me how the mirror works again?"
Unknown Voice 2: "Dude, it's simple. A becomes Z, B becomes Y. First becomes last."
Unknown Voice 1: "So 'attack at dawn' becomes..."
Unknown Voice 2: "zggzxp zg wzdm. See? Easy."
Unknown Voice 1: "That's actually kind of cool."
Unknown Voice 2: "Yeah, Ghost came up with it. Thinks he's a genius."
Unknown Voice 1: "Wraith still hate it?"
Unknown Voice 2: "Wraith hates everything."
```
#### YOUR TASK

Create a program called `void_decipher.py` that:

- Reads the intercepted file `thevoid_conversation.txt`
- Decodes each message based on our evidence
- Prints the conversation in real-time as it unfolds, with timestamps
- Saves the full decoded conversation to `void_decoded.txt`
- Key intelligence extracted (what are they planning? when? where? what equipment?)


<details>
<summary><b><kbd>🧐 Hint Please!</kbd></b></summary>

> Some Gagdets at Your Disposal: `ord()`, `open(filename, 'r')`, `open(filename, 'w')`

</details>

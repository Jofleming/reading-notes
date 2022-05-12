# Automation

## Python Regular Expressions Tutorial

[Reading](https://www.datacamp.com/tutorial/python-regular-expression-tutorial)

Also known as regex. Are a sequence of characters which check whether a pattern exists in a given text or not. Commonly used in search engines, search and replace tools, validation on e-mail/passwords, and parsing text data files.

To use you need to `import re`.

Ordinary characters can be used to perform simple exact matches.

```
pattern = r"Cookie"
sequence = "Cookie"
if re.match(pattern, sequence):
    print("Match!")
else: print("Not a match!")
```

The `match()` function returns a match object if the text matches the pattern. Otherwise, it returns None.

The r at the start of the first cookie string is called a raw string literal. It changes how the string literal is interpreted. They are stored as they appear. Example is a backslash when prefixed with an r will be seen as just a backslash and not a command.

`search()` will scan through a string/squence, looking for the first location where the reg expression produces a match

`group()` returns a string match by the re.

### Special Characters

Special characters do not match themselves as seen but have a special meaning.

`.` - A period. Matches any single character except the newline char.

`re.search(r'Co.k.e', 'Cookie').group()` - Using period in the cookie example.

`^` - A caret. Matches the START of the string. Useful if you want to make sure a document/sentence starts with certain characters.

`re.search(r'^Eat', "Eat cake!").group()` 

`$` - Matches the END of a string

`re.search(r'cake$', "Cake! Let's eat cake").group()`

`[abc]` - Matches a or b or c.

`[a-zA-Z0-9]` - Matches any letter from (a to z) or (A to Z) or (0 to 9).

TIP: Characters that are not within a range can be matched by complementing the set. If the first character of the set is ^, all the characters that are not in the set will be matched.

`\` Backslash. Perhaps, the most diverse metacharacter!!

* If the character following the backslash is a recognized escape character, then the special meaning of the term is taken (Scenario 1)
* Else if the character following the `\` is not a recognized escape character, then the `\` is treated like any other character and passed through (Scenario 2).
* `\` can be used in front of all the metacharacters to remove their special meaning (Scenario 3).

```
## (Scenario 1) This treats '\s' as an escape character, '\s' defines a space
re.search(r'Not a\sregular character', 'Not a regular character').group()

-> 'Not a regular character'

## (Scenario 2) '\' is treated as an ordinary character, because '\r' is not a recognized escape character
re.search(r'Just a \regular character', 'Just a \regular character').group()

-> 'Just a \regular character'

## (Scenario 3) '\s' is escaped using an extra `\` so its interpreted as a literal string '\s'
re.search(r'Just a \\sregular character', 'Just a \sregular character').group()

-> 'Just a \\sregular character'
```

There is a predefined set of special sequences that begin with '\' and are also very helpful when performing search and match.

`\w` Lowercase 'w'. Matches any single letter, digit, or underscore.

`\W` \W - Uppercase 'W'. Matches any character not part of `\w` (lowercase w).

`\s` Lowercase 's'. Matches a single whitespace character like: space, newline, tab, return.

`\S` Uppercase 'S'. Matches any character not part of `\s` (lowercase s).

```
print("Lowercase s:", re.search(r'Eat\scake', 'Eat cake').group())
print("Uppercase S:", re.search(r'cook\Se', "Let's eat cookie").group())

-> Lowercase s: Eat cake
-> Uppercase S: cookie
```

`\d` Lowercase d. Matches decimal digit 0-9.

`\D` Uppercase d. Matches any character that is not a decimal digit.

`\t` Lowercase t. Matches tab.

`\n` Lowercase n. Matches newline.

`\r` Lowercase r. Matches return.

`\A` Uppercase a. Matches only at the start of the string. Works across multiple lines as well.

TIP: ^ and \A are effectively the same, and so are $ and \Z. Except when dealing with MULTILINE mode. Learn more about it in the flags section.

`\Z` Uppercase z. Matches only at the end of the string.

`\b` Lowercase b. Matches only the beginning or end of the word.

### Repititions

`+` Checks if the preceding character appears one or more times starting from that position.

`re.search(r'Co+kie', 'Cooookie').group()` -> Cooookie

`*` Checks if the preceding character appears zero or more times starting from that position.

`?` Checks if the preceding character appears exactly zero or one time starting from that position.


But what if you want to check for an exact number of sequence repetition?

For example, checking the validity of a phone number in an application. re module handles this very gracefully as well using the following regular expressions:

`{x}` - Repeat exactly x number of times.
`{x,}` - Repeat at least x times or more.
`{x, y}` - Repeat at least x times but no more than y times.

`re.search(r'\d{9,10}', '0987654321').group()` -> '0987654321'

The `+` and `*` qualifiers are said to be greedy

### Grouping in RE

Parts of a regular expression pattern bounded by parenthesis () are called groups. The parenthesis does not change what the expression matches, but rather forms groups within the matched sequence.

example from reading:
```
statement = 'Please contact us at: support@datacamp.com'
match = re.search(r'([\w\.-]+)@([\w\.-]+)', statement)
if statement:
  print("Email address:", match.group()) # The whole matched text
  print("Username:", match.group(1)) # The username (group 1)
  print("Host:", match.group(2)) # The host (group 2)

Email address: support@datacamp.com
Username: support
Host: datacamp.com
```

Another way of doing the same is with the usage of `<>` brackets instead. This will let you create named groups. Named groups will make your code more readable. The syntax for creating named group is: `(?P<name>...)`. Replace the name part with the name you want to give to your group. The ... represent the rest of the matching syntax. See this in action using the same example as before.

```
statement = 'Please contact us at: support@datacamp.com'
match = re.search(r'(?P<email>(?P<username>[\w\.-]+)@(?P<host>[\w\.-]+))', statement)
if statement:
  print("Email address:", match.group('email'))
  print("Username:", match.group('username'))
  print("Host:", match.group('host'))
```

TIP: You can always access the named groups using numbers instead of the name. But as the number of groups increases, it gets harder to handle them using numbers alone. So, always make it a habit to use named groups instead.

### Functions by re

`search()` versus `match()`

The `match()` function checks for a match only at the beginning of the string (by default), whereas the `search()` function checks for a match anywhere in the string.

`findall(pattern, string, flags=0)`

Finds all the possible matches in the entire sequence and returns them as a list of strings. Each returned string represents one match.

`finditer(string, [position, end_position])`

Similar to `findall()` - it finds all the possible matches in the entire sequence but returns regex match objects as an iterator.

TIP: `finditer()` might be an excellent choice when you want to have more information returned to you about your search. The returned regex match object holds not only the sequence that matched but also their positions in the original text.

`sub(pattern, repl, string, count=0, flags=0)`
`subn(pattern, repl, string, count=0)`

`sub()` is the substitute function. It returns the string obtained by replacing or substituting the leftmost non-overlapping occurrences of pattern in string by the replacement repl. If the pattern is not found, then the string is returned unchanged.

The `subn()` is similar to `sub()`. However, it returns a tuple containing the new string value and the number of replacements that were performed in the statement.

```
statement = "Please contact us at: xyz@datacamp.com"
new_email_address = re.sub(r'([\w\.-]+)@([\w\.-]+)', r'support@datacamp.com', statement)
print(new_email_address)

-> Please contact us at: support@datacamp.com
```

`split(string, [maxsplit = 0])`

This splits the strings wherever the pattern matches and returns a list. If the optional argument maxsplit is nonzero, then the maximum 'maxsplit' number of splits are performed.

`start()` - Returns the starting index of the match.
`end()` - Returns the index where the match ends.
`span()` - Return a tuple containing the (start, end) positions of the match.

## Shutil

[Reading](https://pymotw.com/3/shutil/)

## Automation Ideas

[Video](https://www.youtube.com/watch?v=qbW6FRbaSl0&t=69s)




[Back](README.md)
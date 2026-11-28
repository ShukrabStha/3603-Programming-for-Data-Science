# 📝 Worksheet: 05 - Loops and Iteration

Use this worksheet to reinforce your understanding of `for` loops, `while` loops, and reading files. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🔁 Section 1: For Loops

1. What does `range(5)` produce?  
   `Answer:` ___0,1,2,3,4______

2. Write a `for` loop that prints numbers 1 to 10, but skips 5.

```python
# Your code:
```
for i in range(1, 11):
    if i == 5:
        continue
    print(i)

3. What's the difference between using `range(len(my_list))` and just using `enumerate(my_list)` when you need the index?  
   `Answer:` _________range(len(my_list)) only provides the index, while enumerate(my_list) provides both the index and the value. Using enumerate() makes the code simpler._______

---

### ✏️ Task: Numbered Report with enumerate()

```python
# Given: tasks = ["Write report", "Review code", "Attend meeting"]
# Print each task numbered starting at 1, like:
# "1. Write report"
```
tasks = ["Write report", "Review code", "Attend meeting"]

for i, task in enumerate(tasks, start=1):
    print(f'{i}. {task}')

### ✏️ Task: Two Lists with zip()

```python
# Given: cities = ["Austin", "Dallas", "Houston"]
#        populations = [978000, 1300000, 2300000]
# Print a line per city like "Austin: 978,000" (use a format spec for the comma).
```
cities = ["Austin", "Dallas", "Houston"]
populations = [978000, 1300000, 2300000]

for city, population in zip(cities, populations):
    print(f'{city}: {population:,}')

### 🤖 Explain It

In your own words: if you've written C++, compare Python's `for x in list:` to a C++ index-based `for` loop. What has to be managed by hand in C++ that Python handles for you?
Ans: In a classic C++ index-based loop, I have to initialize the index, check the condition, increment the index, and access each item using its index. Python handles the iteration automatically and gives me each item directly, making the code easier to write and understand.

---

## 🔁 Section 2: While Loops

4. What's the difference between a `for` loop and a `while` loop?  
   `Answer:` ____A for loop iterates over a sequence of items, while a while loop repeats as long as its condition is true._____

5. What happens if a `while` loop's condition never becomes `False`?  
   `Answer:` ___It creates an infinite loop that continues running until it is manually stopped or interrupted.____

---

### ✏️ Task: Countdown with While

```python
# Use a while loop to count down from 5 to 1.
```
n = 5

while n >= 1:
    print(n)
    n -= 1

### ✏️ Task: Sentinel Loop

```python
# Use a while True loop with input() to collect names from the user
# until they type "stop". Print the final list of names collected.
```
names = []

while True:
    name = input("Enter a name (or 'stop' to finish): ")

    if name == 'stop':
        break

    names.append(name)

print('Names collected:', names)

### 🤖 Explain It

In your own words: why does a sentinel loop use `while True:` with a `break` inside, instead of putting the stop condition directly in the `while` line? Is there a situation where you *could* put it directly in the `while` line instead?
Ans: A sentinel loop uses while True because the program needs to collect input before checking whether the user wants to stop. The break statement ends the loop when the sentinel value is entered. We could also put the condition directly in the while line by using the walrus operator or initializing the input variable before the loop.

---

## 📁 Section 3: File Reading and `with`

6. What does the `with` statement do when opening a file?  
   `Answer:` ________The with statement automatically closes the file when the block finishes, even if an error occurs.______

7. How do you loop over each line in a file?  
   `Answer:` __with open('sample.txt', 'r') as f:
    for line in f:
        print(line.strip())

8. What error do you get if you try to open a file that doesn't exist, and how would you handle it without crashing the program?  
   `Answer:` __Python raises a FileNotFoundError. We can handle it using try and except._____
   try:
    with open('sample.txt', 'r') as f:
        print(f.read())
except FileNotFoundError:
    print('File not found.')

---

### ✏️ Task: File Filter

```python
# Using the sample.txt file from the notebook (or create your own),
# write code that prints only the lines containing the word "error".
```
with open('sample.txt', 'r') as f:
    for line in f:
        if 'error' in line:
            print(line.strip())

### ✏️ Task: Word Count

```python
# Loop over sample.txt and print the total number of words across
# the entire file (hint: len(line.split()) per line, added up).
```
word_count = 0

with open('sample.txt', 'r') as f:
    for line in f:
        word_count += len(line.split())

print('Total words:', word_count)

### 🤖 Explain It

In your own words: what specifically goes wrong if you open a file *without* using `with` (or without manually calling `.close()`) and your code crashes partway through reading it?
Ans:If I open a file without using with or manually closing it, an error could interrupt the program before the file is closed. This can waste system resources and may cause problems when accessing the file again. Using with automatically closes the file even when an error happens.

---

## 🚀 Section 4: Going Further (Optional)

This pairs with the "🔥 Challenge" section in the While Loops notebook — skip if you haven't gotten there yet.

### ✏️ Task: Walrus Operator

```python
# Rewrite this using the walrus operator (:=) so it's a single while line
# instead of a while True + break:
# while True:
#     n = int(input("Enter a number (0 to stop): "))
#     if n == 0:
#         break
#     print(n * n)
```
Ans:
while (n := int(input("Enter a number (0 to stop): "))) != 0:
    print(n * n)

---

## 🧾 Submit Checklist

- [#] I wrote a `for` loop using `range()`.
- [#] I used `enumerate()` at least once.
- [#] I used `zip()` to loop over two sequences together.
- [#] I wrote a `while` loop, including at least one with `break` or `continue`.
- [#] I read a file with `with open(...)` and looped over its lines.
- [#] I completed the "Explain It" prompts in my own words.

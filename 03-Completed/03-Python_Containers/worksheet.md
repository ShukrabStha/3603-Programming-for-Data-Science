# 📝 Worksheet: 01 - Working with Data

Use this worksheet to review and reinforce your understanding of Python's core data containers. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: Lists

1. What method adds an item to the end of a list?  
   `Answer:` ____.append()__________________

2. How can you remove an item from a list by value? By position?  
   `Answer:` __: Use .remove(value) to remove an item by value and .pop(index) or del to remove an item by position.___

3. What's the result of this code?

```python
nums = [2, 4, 6]
nums.append(8)
print(nums)
```

   `Answer:` _______[2,4,6,8]_____________________

4. What does `my_list[1:4]` return, given `my_list = [10, 20, 30, 40, 50]`?  
   `Answer:` ________[20,30,40]____________________

4a. Given `a = [1, 2]` and `b = [3, 4]`, what is the result of `a + b`? Of `a.append(b)`? Of `a.extend(b)`?  
   `Answer:` ________Assuming each operation starts with the original lists:
- a + b: Creates [1, 2, 3, 4] without modifying a.
- a.append(b): Changes a to [1, 2, [3, 4]].
- a.extend(b): Changes a to [1, 2, 3, 4].
Both .append() and .extend() return None._________

4b. Given `grid = [[1, 2], [3, 4]]`, how do you access the value `3`?  
   `Answer:` ______grid[1][0]______________________

4c. List three different ways to remove an item from a list.  
   `Answer:` ____.remove(), .pop(),_and del__________

---

### ✏️ Task: List Practice

```python
# Create a list of your top 3 favorite foods.
# Add another food to the list.
# Remove one item and print the list.
```
foods = ['Momo', 'Pizza', 'Pasta']

foods.append('Burger')
foods.remove('Pizza')

print(foods)

### ✏️ Task: Slicing and Sorting

```python
# Given: numbers = [42, 17, 8, 99, 23, 4]
# 1. Print the first three numbers using slicing.
# 2. Print the numbers sorted from smallest to largest.
# 3. Print the numbers sorted from largest to smallest.
```
numbers = [42, 17, 8, 99, 23, 4]

print(numbers[:3])
print(sorted(numbers))
print(sorted(numbers, reverse=True))

### ✏️ Task: Filtering

```python
# Given: temps = [55, 72, 90, 43, 88, 67, 101]
# Build a new list called "hot" containing only temps over 85.
# Print "hot".
```
temps = [55, 72, 90, 43, 88, 67, 101]

hot = [temp for temp in temps if temp > 85]

print(hot)

### ✏️ Task: Combine Lists Three Ways

```python
# Given: morning = ['eggs', 'toast']
#        extras  = ['jam', 'coffee']
# 1. Use + to make a new list "breakfast" without changing "morning".
# 2. On a fresh copy of "morning", use .append(extras) and print the result.
#    Notice how many items the list has now, and why.
# 3. On another fresh copy, use .extend(extras) and print the result.
```
morning = ['eggs', 'toast']
extras = ['jam', 'coffee']

# 1. Combine using +
breakfast = morning + extras
print(breakfast)
print(morning)

# 2. Combine using append()
morning_copy = morning.copy()
morning_copy.append(extras)
print(morning_copy)
print(len(morning_copy))

# 3. Combine using extend()
morning_copy = morning.copy()
morning_copy.extend(extras)
print(morning_copy)

### ✏️ Task: 2D List (grid)

```python
# board = [
#     [1, 2, 3],
#     [4, 5, 6],
#     [7, 8, 9],
# ]
# 1. Print the value in row 2, column 0.
# 2. Change the center value to 0.
# 3. Loop over the board and print each row on its own line.
```
board = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
]

print(board[2][0])

board[1][1] = 0

for row in board:
    print(row)

### ✏️ Task: Deleting Items

```python
# Given: queue = ['Ana', 'Ben', 'Cy', 'Dana', 'Eve']
# 1. Remove 'Cy' by value.
# 2. Use .pop() to remove and capture the last person into a variable "served".
# 3. Use del to remove the first person.
# 4. Print the remaining queue and "served".
```
queue = ['Ana', 'Ben', 'Cy', 'Dana', 'Eve']

queue.remove('Cy')
served = queue.pop()
del queue[0]

print("Remaining queue:", queue)
print("Served:", served)

### ✏️ Task: Iterate by Index

```python
# Given: prices = [10, 20, 30, 40]
# 1. Use "for i in range(len(prices)):" to print each item as "0: 10", "1: 20", ...
# 2. Using the index, add 5 to every price in place, then print the list.
# 3. Rewrite step 1 using enumerate() instead.
```
prices = [10, 20, 30, 40]

# 1. Print using indexes
for i in range(len(prices)):
    print(f"{i}: {prices[i]}")

# 2. Add 5 to each price
for i in range(len(prices)):
    prices[i] += 5

print(prices)

# 3. Print using enumerate()
for i, price in enumerate(prices):
    print(f"{i}: {price}")

### 🤖 Explain It

In your own words: what's the difference between a list and a slice of a list? Is slicing a list the same as modifying it? And when you write `a.append(b)` versus `a.extend(b)`, what ends up in `a` each way?
Ans:A list contains a collection of items, while a slice creates a new list containing selected items from the original list. Slicing does not directly modify the original list. When we use a.append(b), the entire list b is added as one item. When we use a.extend(b), each item from b is added separately to a.

---

## 🔒 Section 2: Tuples

5. What is a key difference between a list and a tuple?  
   `Answer:` ___________Lists are mutable, while tuples are immutable. Lists use square brackets, and tuples are commonly written using parentheses._________________

6. Can you change the contents of a tuple once it is created? Why or why not?  
   `Answer:` ___________No, we cannot replace, add, or remove tuple elements because tuples are immutable.________________

7. What does `first, *rest = (10, 20, 30, 40)` assign to `first` and `rest`?  
   `Answer:` ___________first = 10
rest = [20, 30, 40]_________________

---

### ✏️ Task: Tuple Practice

```python
# Create a tuple with your favorite 3 numbers.
# Unpack it into three variables and print each.
```
numbers = (7, 10, 21)

a, b, c = numbers

print(a)
print(b)
print(c)

### ✏️ Task: Unpacking with *rest

```python
# Given: race_times = (9.58, 9.63, 9.69, 9.71, 9.74)
# Unpack this into "winner" (the first time) and "others" (everything else).
# Print both.
```
race_times = (9.58, 9.63, 9.69, 9.71, 9.74)

winner, *others = race_times

print("Winner:", winner)
print("Others:", others)

### ✏️ Task: Tuples as Dictionary Keys

```python
# Build a dictionary called "distances" where the keys are (city1, city2)
# tuples and the values are the distance in miles between them.
# Add at least two entries, then look up and print one of them.
```
distances = {
    ('Dallas', 'Houston'): 240,
    ('Dallas', 'Austin'): 195
}

print(distances[('Dallas', 'Houston')])

### 🤖 Explain It

In your own words: why does Python allow a tuple to be a dictionary key, but not a list? What property makes that possible?
Ans:Tuples can be used as dictionary keys because they are immutable and hashable when all their elements are hashable. Lists can be changed after they are created, so they are not hashable and cannot be used as dictionary keys.

---

## 🔑 Section 3: Dictionaries

8. What does the `.get()` method do differently from accessing a key directly with `[]`?  
   `Answer:` ___________The .get() method returns None or a specified default value if the key does not exist. Using square brackets raises a KeyError when the key is missing.____________

9. How do you loop through both keys and values in a dictionary?  
   `Answer:` _________use  the .items() method.
   for key, value in student.items():
    print(key, value)____

10. How would you remove a key from a dictionary and also capture the value it held?  
    `Answer:` __________use the .pop()method. 
     removed_value = student.pop('age')__________________

11. In a list of dictionaries like `people = [{'name': 'Ana'}, {'name': 'Ben'}]`, how do you get Ben's name?  
    `Answer:` __________people[1]['name']__________________

12. If the same dictionary object is stored in both a list and another dictionary, and you change it through one, does the other see the change? Why?  
    `Answer:` __________Yes. Both containers reference the same dictionary object in memory. Changing the dictionary through one container also makes the change visible through the other.__________________

---

### ✏️ Task: Dictionary Practice

```python
# Create a dictionary with keys: 'name', 'age', and 'hobby'.
# Print each key and value in the format "key: value".
```
student = {
    'name': 'Alex',
    'age': 21,
    'hobby': 'Programming'
}

for key, value in student.items():
    print(f"{key}: {value}")

### ✏️ Task: Build from Two Lists

```python
# Given: products = ['pen', 'notebook', 'eraser']
#        prices = [1.50, 3.25, 0.75]
# Build a dictionary mapping each product to its price.
# Print the total cost of all products (hint: sum the .values()).
```
products = ['pen', 'notebook', 'eraser']
prices = [1.50, 3.25, 0.75]

product_prices = dict(zip(products, prices))

total = sum(product_prices.values())

print(product_prices)
print(f"Total cost: ${total:.2f}")

### ✏️ Task: Nested Dictionaries

```python
# Given:
# inventory = {
#     'apples': {'count': 50, 'price': 0.50},
#     'bananas': {'count': 30, 'price': 0.25},
# }
# Loop through inventory and print a line for each fruit like:
# "apples: 50 units at $0.50"
```
inventory = {
    'apples': {'count': 50, 'price': 0.50},
    'bananas': {'count': 30, 'price': 0.25},
}

for fruit, info in inventory.items():
    print(f"{fruit}: {info['count']} units at ${info['price']:.2f}")
### ✏️ Task: List of Dictionaries (table rows)

```python
# roster = [
#     {'name': 'Alex', 'major': 'CS'},
#     {'name': 'Ana',  'major': 'Math'},
#     {'name': 'Ben',  'major': 'History'},
# ]
# 1. Loop over roster and print "name - major" for each student.
# 2. Add a new student record to the list.
# 3. Build and print a list of just the names of everyone majoring in 'CS'.
```
roster = [
    {'name': 'Alex', 'major': 'CS'},
    {'name': 'Ana', 'major': 'Math'},
    {'name': 'Ben', 'major': 'History'},
]

# 1. Print each student
for student in roster:
    print(f"{student['name']} - {student['major']}")

# 2. Add a new student
roster.append({'name': 'Dana', 'major': 'CS'})

# 3. Filter CS students
cs_students = [
    student['name']
    for student in roster
    if student['major'] == 'CS'
]

print("CS students:", cs_students)

### ✏️ Task: Update a Record by Row Number

```python
# Using the roster above:
# 1. Build a dict "by_row" mapping each row number to its record
#    (hint: {i: row for i, row in enumerate(roster)}).
# 2. Change the major of the student in row 2 to 'CS'.
# 3. Print roster[2] and explain why it changed too.
```
by_row = {i: row for i, row in enumerate(roster)}

by_row[2]['major'] = 'CS'

print(roster[2])

# Both by_row[2] and roster[2] reference the same
# dictionary object, so both show the updated major.

### 🤖 Explain It

In your own words: what's the difference between `student['gpa']` and `student.get('gpa')` when `'gpa'` isn't in the dictionary? Which would you use, and when? Also: why does changing `by_row[2]` also change `roster[2]`?
Ans: If 'gpa' does not exist, student['gpa'] raises a KeyError, while student.get('gpa') returns None. I would use square brackets when I know the key exists and .get() when the key might be missing. Changing by_row[2] also changes roster[2] when updating its fields because both reference the same dictionary object.

---

## 🚀 Section 4: Going Further (Optional)

These pair with the "🔥 Challenge" sections in the notebooks — skip if you haven't gotten there yet.


### ✏️ Task: List Comprehension

```python
# Rewrite this loop as a one-line list comprehension:
# cubes = []
# for n in range(6):
#     cubes.append(n ** 3)
```
cubes = [n ** 3 for n in range(6)]

print(cubes)

### ✏️ Task: namedtuple

```python
# Create a namedtuple called "Book" with fields "title" and "author".
# Make one instance and print both fields by name.
```
from collections import namedtuple

Book = namedtuple('Book', ['title', 'author'])

book = Book('Atomic Habits', 'James Clear')

print(book.title)
print(book.author)

### ✏️ Task: Word Counter

```python
# text = "to be or not to be that is the question"
# Build a dictionary counting how many times each word appears.
# (Try it by hand first, then check yourself with collections.Counter.)
```
from collections import Counter

text = "to be or not to be that is the question"

words = text.split()
counts = {}

for word in words:
    counts[word] = counts.get(word, 0) + 1

print(counts)

# Check using Counter
print(Counter(words))

### ✏️ Task: Parse Some JSON

```python
import json
raw = '''
{
  "course": "Programming for Data Science",
  "online": true,
  "instructor": null,
  "students": [
    {"name": "Alex", "grade": 91},
    {"name": "Ana",  "grade": 88}
  ]
}
'''
# 1. Use json.loads(raw) to turn this into Python objects.
# 2. Print the course name and the second student's grade.
# 3. Print the Python type of the value that came from "online" and from "instructor".
# 1. Convert JSON into Python objects
data = json.loads(raw)

# 2. Print course name and second student's grade
print(data['course'])
print(data['students'][1]['grade'])

# 3. Print Python data types
print(type(data['online']))
print(type(data['instructor']))
```

### ✏️ Task: Walk a GeoJSON FeatureCollection

```python
geo = {
    "type": "FeatureCollection",
    "features": [
        {"type": "Feature",
         "geometry": {"type": "Point", "coordinates": [-98.529, 33.878]},
         "properties": {"name": "Bolin Hall"}},
        {"type": "Feature",
         "geometry": {"type": "Point", "coordinates": [-98.531, 33.876]},
         "properties": {"name": "Moffett Library"}},
    ],
}
for feature in geo["features"]:
    name = feature["properties"]["name"]
    longitude, latitude = feature["geometry"]["coordinates"]

    print(f"{name}: Latitude = {latitude}, Longitude = {longitude}")
# Loop over geo["features"] and print each building's name with its
# latitude and longitude. Remember: coordinates are [longitude, latitude].
```

---

## 🧾 Submit Checklist

- [#] I practiced creating, slicing, sorting, and filtering lists.
- [#] I can explain the difference between `+`, `append()`, and `extend()`.
- [#] I built and traversed a nested (2D) list.
- [#] I removed list items with `remove()`, `pop()`, and `del`.
- [#] I looped by index with `range(len(...))` and with `enumerate()`.
- [#] I understand how tuples are different from lists, and why that makes them hashable.
- [#] I accessed, looped through, updated, and removed items from a dictionary.
- [#] I built a dictionary from two separate lists.
- [#] I worked with at least one nested dictionary.
- [#] I processed a list of dictionaries as table rows and updated a record by row number.
- [#] I parsed JSON with `json.loads()` and walked a GeoJSON FeatureCollection.
- [#] I completed the "Explain It" prompts in my own words.

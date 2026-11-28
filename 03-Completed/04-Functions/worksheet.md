# 📝 Worksheet: 04 - Functions

Use this worksheet to reinforce your understanding of defining and calling functions, flexible arguments, and type-based behavior. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: Function Basics

1. What's the difference between a parameter and an argument?  
   `Answer:` _______A parameter is a variable defined in a function, while an argument is the actual value passed to the function when it is called._______________

2. What does this function return if called as `mystery(5)`?

```python
def mystery(x):
    y = x * 2
    print(y)
```

   `Answer:` ______None. The function prints 10 but does not return a value.______ (careful — this is a trick question)

3. Rewrite this so it actually returns a usable value instead of just printing it:

```python
def area(length, width):
    print(length * width)
```

   `Answer:` __def area(length, width):
return length * width______

---

### ✏️ Task: Default Values

```python
# Write a function `power(base, exponent=2)` that returns base raised to exponent.
# Call it once with just a base (should square it), and once with both arguments.
```
def power(base, exponent=2):
    return base ** exponent

print(power(5))
print(power(5, 3))

### ✏️ Task: Scope

```python
# Predict, then check: what does this print?
count = 0
def increment():
    count = count + 1
    return count
print(increment())
print(count)
# (Hint: this is the local-vs-global lesson biting you. You do NOT need to fix it yet.)
```
count = 0

def increment():
    count = count + 1
    return count

print(increment())
print(count)

### 🤖 Explain It

In your own words: why did the "Task: Scope" code above not update the outer `count`? What would you have to do differently if you actually wanted to change a global variable from inside a function?
Ans:The code does not update the outer count because Python treats count inside the function as a local variable. It tries to use the local variable before assigning a value to it. To change the global variable, I would need to use global count inside the function.

---

## 🔁 Section 2: Flexible Arguments

4. What does `*args` collect its extra arguments into?  
   `Answer:` ________A tuple.______

5. What does `**kwargs` collect its extra arguments into?  
   `Answer:` ________A dictionary._____

6. What will this print?

```python
def describe(**info):
    print(info)

describe(name='Ada', role='Mathematician')
```

   `Answer:` ______{'name': 'Ada', 'role': 'Mathematician'}_________________

---

### ✏️ Task: Variable-Length Averaging

```python
# Write a function `average(*nums)` that returns the average of any amount of numbers.
# Test it with 2 numbers, then with 6.
```
def average(*nums):
    if not nums:
        return 0
    return sum(nums) / len(nums)

print(average(10, 20))
print(average(10, 20, 30, 40, 50, 60))

### ✏️ Task: Flexible Profile Builder

```python
# Write a function `build_profile(name, **details)` that returns a dictionary
# with 'name' plus whatever other keyword arguments were passed in.
# Call it with name plus at least 3 other details (e.g. major='CS', year=2).
```
def build_profile(name, **details):
    return {'name': name, **details}

profile = build_profile(
    'Alex',
    major='Computer Science',
    year=3,
    university='MSU'
)

print(profile)

### 🤖 Explain It

In your own words: why does Python require regular parameters first, then `*args`, then `**kwargs` — what would go wrong if you could put them in any order?
Ans:Python uses this order so it can clearly understand which arguments belong to regular parameters, which extra positional arguments belong to *args, and which extra keyword arguments belong to **kwargs. Without these ordering rules, assigning arguments to parameters could become confusing. Python also allows keyword-only parameters after *args.

---

## 🎭 Section 3: Type-Based Behavior

7. Why can't you define two functions both named `calculate_area`, one for circles and one for rectangles, the way you could in C++?  
   `Answer:` ________Python does not support traditional function overloading based on parameter types. If two functions have the same name, the second definition replaces the first. We can use conditional statements or type checks inside one function instead._______________

8. What will this print?

```python
def classify(x):
    if isinstance(x, bool):
        return 'boolean'
    elif isinstance(x, int):
        return 'integer'
    else:
        return 'something else'

print(classify(True))
```

   `Answer:` ________boolean______ (careful — `bool` is technically a subclass of `int` in Python, which is why the `bool` check has to come first)

9. What's one advantage of `isinstance(x, (int, float))` over just `isinstance(x, int)` when checking "is this a number"?  
   `Answer:` ________It checks for both integers and floating-point numbers instead of checking only integers._______

---

### ✏️ Task: Type-Branching Function

```python
# Write a function `describe_input(x)` that:
#   - if x is a list, prints how many items it has
#   - if x is a string, prints how many characters it has
#   - if x is a number, prints whether it's positive, negative, or zero
# Test it on a list, a string, and a number.
```
def describe_input(x):
    if isinstance(x, list):
        print(f'The list has {len(x)} items.')

    elif isinstance(x, str):
        print(f'The string has {len(x)} characters.')

    elif isinstance(x, (int, float)):
        if x > 0:
            print('The number is positive.')
        elif x < 0:
            print('The number is negative.')
        else:
            print('The number is zero.')

describe_input([1, 2, 3, 4])
describe_input('Python')
describe_input(-10)

### ✏️ Task: Compare to dict.get()

```python
# Given: settings = {'theme': 'dark'}
# 1. Use settings.get('font_size', 12) to get a font size with a fallback.
# 2. Write a function get_display_name(value) that returns str(value) if value
#    is a number, or value itself if it's already a string.
# In a comment, explain how these two are "the same kind of decision."
settings = {'theme': 'dark'}

font_size = settings.get('font_size', 12)
print(font_size)

def get_display_name(value):
    if isinstance(value, (int, float)):
        return str(value)
    elif isinstance(value, str):
        return value

print(get_display_name(42))
print(get_display_name('Python'))

# Both use the available information to make a decision.
# dict.get() checks whether a key exists and uses a fallback.
# isinstance() checks the type and chooses the correct behavior.
```

### 🤖 Explain It

In your own words: what is duck typing, and can you think of a real-world (non-code) example of judging something by how it behaves rather than by its label?
Ans:Duck typing means judging an object based on what it can do instead of checking its specific type. A real-world example is choosing someone to play basketball based on their ability to play rather than whether they are officially called a basketball player.

---

## 🚀 Section 4: Going Further (Optional)

These pair with the "🔥 Challenge" sections in the notebooks — skip if you haven't gotten there yet.

### ✏️ Task: Mutable Default Gotcha

```python
# Given this buggy function:
def add_tag(tag, tags=[]):
    tags.append(tag)
    return tags

# Call add_tag('python') twice in a row and print the result each time.
# Then rewrite the function using tags=None so each call starts fresh.
```
# Buggy function
def add_tag(tag, tags=[]):
    tags.append(tag)
    return tags

print(add_tag('python'))
print(add_tag('python'))

# Fixed function
def add_tag(tag, tags=None):
    if tags is None:
        tags = []

    tags.append(tag)
    return tags

print(add_tag('python'))
print(add_tag('python'))

### ✏️ Task: Unpacking Into a Call

```python
# Given: def volume(length, width, height): return length * width * height
# Given: dimensions = [3, 4, 5]
# Call volume() by unpacking "dimensions" with *, instead of writing out
# volume(dimensions[0], dimensions[1], dimensions[2]).
```
def volume(length, width, height):
    return length * width * height

dimensions = [3, 4, 5]

print(volume(*dimensions))

---

## 🧾 Submit Checklist

- [#] I wrote a function that returns a value (not just prints one).
- [#] I wrote a function with a default parameter value.
- [#] I wrote a function using `*args` and one using `**kwargs`.
- [#] I wrote a function that branches its behavior based on `isinstance()`.
- [#] I completed the "Explain It" prompts in my own words.

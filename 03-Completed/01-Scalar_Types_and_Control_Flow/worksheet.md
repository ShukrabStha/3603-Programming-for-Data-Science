# 📝 Worksheet: 02 - Scalar Types and Control Flow

Use this worksheet to reinforce your understanding of variables, arithmetic, comparisons, and decision logic. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: Scalar Types and Casting

1. What is the output of the following code?

```python
x = 10
print(type(x))
```

   `Answer:`__<class_'int'>___

2. What scalar type would best represent:
   - A person's name: ___str____
   - Their age: ___int____
   - Whether they passed a test: _bool______

3. Why does `int('21')` work, but `int('twenty-one')` raise an error?  
   `Answer:` ___int('21')works because the string contains digits representing an integer. 'twenty-one' contains words, so python raises a ValueError___

---

### ✏️ Task: Type Practice

```python
# Create a variable for each type and print its value and type.
# Example: an int, float, str, and bool.
age = 20
height = 5.8
name = "Shukrab"
passed = True

print(age, type(age))
print(height, type(height))
print(name, type(name))
print(passed, type(passed))

### ✏️ Task: Arithmetic

```python
# Given: hours_worked = 37, hourly_rate = 15.50
# Print the total pay.
# Print the total pay rounded to 2 decimal places (hint: round()).

hours_worked = 37
hourly_rate = 15.50
total_pay = hours_worked * hourly_rate
print(total_pay)
print(round(total_pay,2))

#Practice integer division and remainder.
print(hours_worked // 8)  # 4 complete 8-hours periods
print(hours_worked % 8) # 5 hours left over

### ✏️ Task: Casting Round Trip

```python
# Given: user_input = "3.14159"
# Convert it to a float, then print it rounded to 2 decimal places.
```
user_input = "3.14159"
number = float(user_input)

print(round(number, 2))

### 🤖 Explain It

In your own words: why does `input()` always return a string, and why does that matter when you want to do math with what the user typed? 

input() returns a string because it reads what the user types as text. If I want to use that input in a calculation, I need to convert it with int() or float(). For example, "5" + "3" gives "53", but converting both values to integers lets me add them to get 8.
---

## 🔁 Section 2: Comparison Operators

4. What does the `!=` operator mean?

   `Answer:` _“not equal to.”________

5. What will the following code print?

```python
a = 5
b = 3
print(a < b or b < 10)
```

   `Answer:` ___________True____________

6. What does `0 <= score <= 100` check, and how would you write the same thing *without* chaining?  
   `Answer:` ____________0 <= score and score <= 100___________

---

### ✏️ Task: Comparison Practice

```python
# Given: temperature = 98.6
# Print True if it's within normal human body temperature range (97.0 to 99.0), else False.
# Try it both as a chained comparison and as two separate comparisons joined with "and".
```

### 🤖 Explain It

In your own words: what's the difference between `=` and `==` in Python? Why does mixing them up cause errors (or worse, silently wrong code)?

= assigns a value to a variable, while == compares two values. For example, score = 70 stores 70, and score == 70 checks whether the score equals 70. Using = in a normal Python if condition causes a syntax error. Using == when I meant to assign a value can leave the variable unchanged.

**If you've written C++:** explain why `0 <= score <= 100` is safe to write in Python but dangerous to write in C++. What does the C++ version actually evaluate to, and how would you fix it?

Python understands 0 <= score <= 100 as two comparisons joined with and. In C++, it is evaluated as:(0 <= score) <= 100
first comparison produces true or false, which becomes 1 or 0 in the second comparison. Both are less than or equal to 100, so this expression evaluates to true regardless of the numeric score.

The correct C++ condition is:
0 <= score && score <= 100
---


## 🔀 Section 3: Control Flow

7. Write a conditional that prints "Pass" if a grade is >= 70, and "Fail" otherwise.

```python
# Your code:
grade = 75

if grade >= 70:
    print("Pass")
else:
    print("Fail")

8. What does `elif` allow you to do that separate `if` statements don't?  
   `Answer:` ________elif lets me check another condition only if the previous conditions were false. An if/`elif`/`else` chain runs only the first matching branch. Separate if statements check their conditions independently, so more than one branch can run._______________

9. What will this print?

```python
age = 16
has_ticket = False
print(age >= 13 and has_ticket)
```

   `Answer:` _________False______________

---

### ✏️ Task: Multi-Branch Logic

```python
# Given: bmi = 22.5
# Print the BMI category:
# "Underweight" (< 18.5), "Normal" (18.5-24.9), "Overweight" (25-29.9), "Obese" (30+)
bmi = 22.5

if bmi < 18.5:
    print("Underweight")
elif bmi < 25:
    print("Normal")
elif bmi < 30:
    print("Overweight")
else:
    print("Obese")

### ✏️ Task: Multi-Line Branches

```python
# Given: cart_items = 3, member_since_days = 400
# In the if-branch (member_since_days >= 365): compute a "loyalty discount" of 15%,
#   print the discount amount, and print the final price.
# In the else-branch: print that there's no discount yet, and print the full price.
# Use item_price = 20.00 per item as the starting subtotal.
# Each branch should have at least 3 lines — this is the same shape as the
# "One Branch, Many Lines" example in the notebook.

cart_items = 3
member_since_days = 400
item_price = 20.00

subtotal = cart_items * item_price

if member_since_days >= 365:
    discount = subtotal * 0.15
    final_price = subtotal - discount
    print(f"Discount amount: ${discount:.2f}")
    print(f"Final price: ${final_price:.2f}")
else:
    final_price = subtotal
    print("There is no discount yet.")
    print(f"Full price: ${final_price:.2f}")

### ✏️ Task: Your Turn

Write a program that asks for the weather and prints:
- "Bring sunscreen" if it's sunny
- "Take an umbrella" if it's raining
- "Check the forecast" otherwise

weather = input("What is the weather? ").strip().lower()

if weather == "sunny":
    print("Bring sunscreen")
elif weather == "raining":
    print("Take an umbrella")
else:
    print("Check the forecast")

### 🤖 Explain It

In your own words: what's the difference between using `and` versus writing nested `if` statements to check two conditions? Do they always produce the same result?

Using and checks whether both conditions are true in one statement. Nested if statements check one condition first, then check the second inside the first branch. Both approaches can produce the same result when the action should happen only if both conditions are true. They do not always behave the same because nested statements can have extra actions or separate else branches. Also, and skips checking the second condition when the first is false.

---

## 🚀 Section 4: Going Further (Optional)

These pair with the "🔥 Challenge" sections in the notebooks — skip if you haven't gotten there yet.

### ✏️ Task: Conditional Expression

```python
# Rewrite this as a one-line conditional expression:
# if temperature > 90:
#     comfort = "too hot"
# else:
#     comfort = "fine"

temperature = 95

comfort = "too hot" if temperature > 90 else "fine"

print(comfort)
```

### ✏️ Task: Float Precision

```python
# Predict, then check: does 0.1 + 0.1 + 0.1 == 0.3 evaluate to True or False in Python?
# Write a "close enough" check instead of using == directly.
```
import math

print(0.1 + 0.1 + 0.1 == 0.3)

# Check whether the values are close enough
print(math.isclose(0.1 + 0.1 + 0.1, 0.3))

### ✏️ Task: Match Statement

```python
# Given: grade_letter = 'B'
# Use match/case to print:
#   "Excellent" for 'A'
#   "Good" for 'B' or 'C'
#   "Needs improvement" for anything else (use the "_" wildcard case)

grade_letter = "B"

match grade_letter:
    case "A":
        print("Excellent")
    case "B" | "C":
        print("Good")
    case _:
        print("Needs improvement")

### 🤖 Explain It

**If you've written C++:** how is Python's `match`/`case` similar to a C++ `switch`? What can `match` do (strings, multiple values per case with `|`) that a plain C++ `switch` can't?

Python’s match and C++’s switch both let me choose a branch based on a value. Python’s match supports strings directly and uses | to match alternatives in one case. A plain C++ switch cannot directly switch on strings, but it can group multiple values using stacked case labels. Python’s match can also match patterns such as lists and tuples, and it does not need break to prevent fall-through.
---

## 🧾 Submit Checklist

- [=] I practiced creating and casting each scalar type.
- [ =] I used arithmetic operators, including `//` and `%`.
- [ =] I wrote conditionals using comparison and logical operators.
- [= ] I used a chained comparison at least once.
- [ =] I wrote at least one branch with multiple lines inside it.
- [ =] I completed the "Explain It" prompts in my own words.

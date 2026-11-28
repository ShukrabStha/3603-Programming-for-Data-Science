# 📝 Quiz: 04 - Functions

22 questions covering function basics, flexible arguments, type-based behavior, and the "going further" topics from the Challenge sections. Mix of multiple choice, true/false, code-tracing, and short answer.

Try every question on your own first — the Answer Key is at the bottom, no peeking. If you're using an AI tutor, paste in *your answer* and ask it to check your reasoning rather than asking it to solve the question first.

---

## Section A — Function Basics

**1.** (Multiple Choice) Which keyword defines a function in Python?
A) `func`  B) `def`  C) `function`  D) `define`
Ans:def

**2.** (Code Tracing) What prints?
```python
def add(a, b):
    return a + b

x = add(2, 3)
print(x)
```
Ans:5

**3.** (Code Tracing) What prints — both lines?
```python
def show(a, b):
    print(a + b)

x = show(2, 3)
print(x)
```
Ans:5
None

**4.** (Short Answer) What's the difference between a function that uses `return` and one that only uses `print()`?
Ans: return sends a value back to the caller so it can be stored or reused. print() only displays the value on the screen.

**5.** (Code Tracing) What prints?
```python
def stats(nums):
    return min(nums), max(nums)

lo, hi = stats([3, 9, 1])
print(hi)
```
Ans:9

**6.** (True/False) A variable created inside a function is accessible outside of it after the function finishes running.
Ans: False. A variable created inside a function is a local variable.

**7.** (Code Tracing) What prints?
```python
def greet(name, greeting='Hi'):
    return f'{greeting}, {name}'

print(greet('Ada'))
```
Ans: Hi, Ada

---

## Section B — Flexible Arguments

**8.** (Code Tracing) What prints?
```python
def total(*args):
    return sum(args)

print(total(1, 2, 3, 4))
```
Ans: 10

**9.** (Short Answer) Inside a function defined with `*args`, what data type is `args`?
Ans: A tuple.

**10.** (Short Answer) Inside a function defined with `**kwargs`, what data type is `kwargs`?
Ans: A dictionary.

**11.** (Multiple Choice) Which parameter order is correct when a function uses all three kinds?
A) `**kwargs, *args, regular`  B) `regular, *args, **kwargs`  C) `*args, regular, **kwargs`  D) Any order works
Ans: regular, *args, **kwargs

**12.** (Code Tracing) What prints?
```python
def f(a, *b, **c):
    print(a, b, c)

f(1, 2, 3, x=4)
```
Ans: 1 (2, 3) {'x': 4}

**13.** (Short Answer) `introduce('Ada', 28)` and `introduce(age=28, name='Ada')` can call the exact same function and produce the same result. What's the difference between these two calls?
Ans:The first call uses positional arguments, where order matters. The second uses keyword arguments, where arguments are matched by parameter names.

---

## Section C — Type-Based Behavior

**14.** (Code Tracing) What prints?
```python
def double(x):
    return x * 2

print(double('ab'))
```
Ans:abab

**15.** (Short Answer) Why doesn't Python support true function overloading the way C++ does (multiple `def`s with the same name but different parameter types)?
Ans:Python does not support traditional function overloading based on parameter types. Defining another function with the same name replaces the previous definition. We can use isinstance() to handle different types inside one function.

**16.** (Multiple Choice) Which is generally the better way to check a value's type inside a function, and why?
A) `type(x) == int`  B) `isinstance(x, int)`
Ans: isinstance(x, int) because it also recognizes subclasses.

**17.** (Short Answer) What is "duck typing," and what phrase is it named after?
Ans: Duck typing means using an object based on its behavior rather than its specific type. It comes from the phrase, "If it walks like a duck and quacks like a duck."

**18.** (Code Tracing) What prints?
```python
def get_len(x):
    try:
        return len(x)
    except TypeError:
        return 'no length'

print(get_len(5))
```
Ans: no length

**19.** (Short Answer) Explain how branching on `isinstance()` inside a function is the "same idea" as `dictionary.get(key, default)`.
Ans: Both check what is available and choose behavior accordingly. dictionary.get() checks whether a key exists, while isinstance() checks whether a value belongs to a particular type.

---

## Section D — Going Further (Bonus)

**20.** (Short Answer) Why is `def add_item(item, cart=[]):` risky if the function appends to `cart` and returns it?
Ans: The default list is created only once when the function is defined. Every call that uses the default list shares it, causing items to accumulate. Using cart=None prevents this problem.

**21.** (Code Tracing) What prints?
```python
def add3(a, b, c):
    return a + b + c

nums = [1, 2, 3]
print(add3(*nums))
```
Ans: 6

**22.** (Short Answer) What's the difference between `*args` appearing in a function's `def` line versus `*nums` appearing in a function *call*?
Ans: In a function definition, *args collects extra positional arguments into a tuple. In a function call, *nums unpacks a list or tuple into separate positional arguments.

---

## ✅ Answer Key

1. **B** — `def`.
2. `5`
3. `8` (printed inside `show`), then `None` (printed outside — `show` never returns anything).
4. `return` hands a value back to the caller so it can be stored or reused; `print()` only displays something on screen and gives the caller nothing back (the function still returns `None`).
5. `9`
6. **False** — that's a local variable; it's gone once the function returns.
7. `Hi, Ada`
8. `10`
9. A tuple.
10. A dictionary.
11. **B** — regular parameters, then `*args`, then `**kwargs`.
12. `1 (2, 3) {'x': 4}`
13. The first uses positional arguments (matched by order); the second uses keyword arguments (matched by name, so order doesn't matter). Same result, different call style.
14. `abab` — `*` on a string repeats it, same as `'ab' * 2`.
15. Python only allows one `def` with a given name in a scope — there's no mechanism to have multiple versions distinguished by parameter type. Type-based branching (`isinstance()` checks) inside a single function is how Python code approximates it.
16. **B** — `isinstance(x, int)`, because it also recognizes subclasses, unlike an exact `type()` comparison.
17. Judging an object by whether it behaves the way you need (e.g. supports `len()`) rather than by its declared type — from "if it walks like a duck and quacks like a duck."
18. `'no length'` — an `int` doesn't support `len()`, so the `except TypeError` branch runs.
19. Both are "check what you actually have, then choose behavior accordingly" patterns: `dict.get()` checks *does this key exist?* and falls back if not; `isinstance()` checks *is this the right type?* and branches if not.
20. Default parameter values are evaluated once, when the function is defined — not on every call. Every call that doesn't pass its own `cart` shares the *same* list, so items pile up across calls instead of starting fresh each time.
21. `6` — `*nums` unpacks the list into three separate positional arguments.
22. In a `def` line, `*args` *collects* any extra positional arguments into a tuple. In a function call, `*nums` does the opposite — it *unpacks* an existing list/tuple into separate positional arguments.

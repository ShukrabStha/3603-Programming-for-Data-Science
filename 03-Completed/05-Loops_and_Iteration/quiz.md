# 📝 Quiz: 05 - Loops and Iteration

20 questions covering for loops, while loops, file loops with `with`, and the "going further" topics from the Challenge sections. Mix of multiple choice, true/false, code-tracing, and short answer.

Try every question on your own first — the Answer Key is at the bottom, no peeking. If you're using an AI tutor, paste in *your answer* and ask it to check your reasoning rather than asking it to solve the question first.

---

## Section A — For Loops

**1.** (Code Tracing) What prints?
```python
for i in range(3, 6):
    print(i)
```
Ans:3
    4
    5

**2.** (Multiple Choice) Which function gives you both the index and the value in a `for` loop?
A) `zip()`  B) `enumerate()`  C) `range()`  D) `index()`
Ans:enumerate()

**3.** (Code Tracing) What prints (both lines)?
```python
for i, f in enumerate(['a', 'b']):
    print(i, f)
```
Ans:0 a
    1 b

**4.** (Code Tracing) What prints (both lines)?
```python
for name, score in zip(['Ana', 'Ben'], [90, 85]):
    print(name, score)
```
Ans:
Ana 90
Ben 85

**5.** (Short Answer) What's the main difference between Python's `for` loop and C++'s classic three-part `for` loop?
Ans:Python's for loop directly iterates over items in a sequence, while C++'s classic for loop requires initialization, a condition, and an increment.

**6.** (True/False) `range(5)` includes the number `5`.
Ans:False. range(5) produces numbers from 0 to 4.

**7.** (Code Tracing) List all the pairs this prints, in order:
```python
for i in range(2):
    for j in range(2):
        print(i, j)
```
Ans:
0 0
0 1
1 0
1 1

---

## Section B — While Loops

**8.** (Code Tracing) What prints?
```python
n = 0
while n < 3:
    print(n)
    n += 1
```
Ans:
0
1
2

**9.** (Short Answer) What causes an infinite loop?
Ans:An infinite loop occurs when the loop's condition never becomes

**10.** (Short Answer) In VS Code, what's the practical fix if you accidentally create one?
Ans:Click the Interrupt/Stop button in VS Code or select Kernel → Interrupt to stop the running cell.

**11.** (Code Tracing) What prints, in order?
```python
n = 0
while n < 5:
    n += 1
    if n == 2:
        continue
    if n == 4:
        break
    print(n)
```
Ans:1
3

**12.** (Multiple Choice) Which loop construct does C++ have that Python has no dedicated version of?
A) `for`  B) `while`  C) `do`/`while`  D) `foreach`
Ans: do/while

**13.** (Short Answer) What is a "sentinel value" in the context of a loop?
Ans:A sentinel value is a special value that tells a loop when to stop, such as 'quit' or 'done'.

---

## Section C — File Loops

**14.** (Short Answer) What does the `with` statement guarantee when you use it to open a file?
Ans:The with statement automatically closes the file when the block finishes, even if an error occurs.

**15.** (Short Answer) When looping over lines in a file, why does `print(line.strip())` usually look better than `print(line)`?
Ans:line.strip() removes leading and trailing whitespace including the newline character, preventing extra blank lines when printing.

**16.** (Short Answer) Why should code that opens a file often be wrapped in `try`/`except`?
Ans:Using try/except allows the program to handle errors, such as missing or unreadable files, without crashing.

**17.** (Multiple Choice) What exception is raised when you try to open a file that doesn't exist?
A) `ValueError`  B) `FileNotFoundError`  C) `IOError`  D) `NameError`
Ans: FileNotFoundError
**18.** (Short Answer) What does `line.strip().split(',')` do to a line of text?
Ans:It removes leading and trailing whitespace from the line and splits the remaining text into a list using commas as separators.
---

## Section D — Going Further (Bonus)

**19.** (Short Answer) What does the walrus operator `:=` do differently from a regular `=`?
Ans:The walrus operator := assigns a value and allows that value to be used within the same expression. Regular = performs an assignment statement.

**20.** (Code Tracing) What prints, in order?
```python
count = 0
while (count := count + 1) <= 3:
    print(count)
```
Ans:
1
2
3
---

## ✅ Answer Key

1. `3`, `4`, `5`
2. **B** — `enumerate()`.
3. `0 a` then `1 b`.
4. `Ana 90` then `Ben 85`.
5. Python's `for` loop is a for-each loop — it hands you each item directly with no index to manage. C++'s classic `for` requires you to declare, check, and increment an index yourself.
6. **False** — `range(5)` is stop-exclusive, so it produces `0, 1, 2, 3, 4`.
7. `0 0`, `0 1`, `1 0`, `1 1`.
8. `0`, `1`, `2`.
9. The loop's condition never becomes `False` — usually because whatever variable the condition depends on is never updated (or updated in a way that never satisfies the exit condition).
10. Click the Interrupt/Stop button next to the running cell (or Kernel → Interrupt) to stop execution.
11. `1`, `3` — `2` is skipped by `continue`, and the loop stops before printing `4` because of `break`.
12. **C** — `do`/`while`.
13. A special value (like `'quit'`) that a loop watches for to know when to stop, typically checked inside a `while True:` loop with `break`.
14. It guarantees the file gets closed automatically once the block ends — even if an error happens inside it — without you having to call `.close()` yourself.
15. Each line from a file includes the trailing newline character; `.strip()` removes it, so `print()` doesn't add an extra blank line on top of it.
16. The file might not exist, might be in the wrong location, or might not be readable — `try`/`except` lets the program handle that gracefully instead of crashing.
17. **B** — `FileNotFoundError`.
18. It first removes leading/trailing whitespace (including the newline), then splits what's left into a list wherever a comma appears.
19. `:=` assigns a value **and** evaluates to that value in the same expression, so you can assign and check a condition in one line instead of two.
20. `1`, `2`, `3` — each pass increments `count` and checks the new value in the same expression; the loop stops once `count` reaches `4`.

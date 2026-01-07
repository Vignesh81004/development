Got it 👍
Below is **ALL 10 exercises solved**, **one by one**, each with:

• Problem
• Backend thinking
• Correct solution
• Test cases
• Key rule learned

This is a **complete backend error-handling reference**.
Save it.

---

# 🧪 Exercise 1: Missing Dictionary Key (KeyError)

### Problem

```python
def get_username(user):
    return user["username"]
```

### Solution

```python
def get_username(user):
    if not isinstance(user, dict):
        return "invalid user"
    try:
        return user["username"]
    except KeyError:
        return "username not found"
```

### Tests

```python
print(get_username("abc"))          # invalid user
print(get_username({}))             # username not found
print(get_username({"username":"a"}))  # a
```

### Rule

Type validation → `if`
Missing key → `try / except`

---

# 🧪 Exercise 2: Wrong Data Type (TypeError)

### Problem

```python
def count_items(data):
    return len(data)
```

### Solution

```python
def count_items(data):
    if not isinstance(data, (list, tuple, str)):
        return "invalid data type"
    return len(data)
```

### Tests

```python
print(count_items([1,2]))   # 2
print(count_items("abc"))   # 3
print(count_items(10))      # invalid data type
```

### Rule

Use `if`, not try/except, for type validation.

---

# 🧪 Exercise 3: Missing Function Argument

### Problem

```python
def create_user(name, email):
    return {"name": name, "email": email}
```

### Solution

```python
def create_user(name, email=None):
    if email is None:
        return "email is missing"
    return {"name": name, "email": email}
```

### Tests

```python
print(create_user("a"))               
print(create_user("a","a@gmail.com"))
```

### Rule

Missing argument ≠ exception
Use default values.

---

# 🧪 Exercise 4: Invalid Value (ValueError)

### Problem

```python
def convert_age(age):
    return int(age)
```

### Solution

```python
def convert_age(age):
    try:
        return int(age)
    except ValueError:
        return "invalid age"
```

### Tests

```python
print(convert_age("20"))   # 20
print(convert_age("abc"))  # invalid age
```

### Rule

Conversion errors → `ValueError`

---

# 🧪 Exercise 5: List + Dictionary Combo

### Problem

```python
def get_first_user_name(users):
    return users[0]["name"]
```

### Solution

```python
def get_first_user_name(users):
    if not isinstance(users, list):
        return "invalid users"
    if len(users) == 0:
        return "no users"
    try:
        return users[0]["name"]
    except KeyError:
        return "name not found"
```

### Tests

```python
print(get_first_user_name("abc"))
print(get_first_user_name([]))
print(get_first_user_name([{}]))
print(get_first_user_name([{"name":"a"}]))
```

### Rule

List validation → length check → key protection

---

# 🧪 Exercise 6: API Input Validation (None)

### Problem

```python
def get_email(email):
    return email.lower()
```

### Solution

```python
def get_email(email):
    if email is None:
        return "email missing"
    if not isinstance(email, str):
        return "invalid email"
    return email.lower()
```

### Tests

```python
print(get_email(None))
print(get_email(123))
print(get_email("A@B.COM"))
```

### Rule

Validation first, processing later.

---

# 🧪 Exercise 7: Nested Dictionary Access

### Problem

```python
def get_city(user):
    return user["address"]["city"]
```

### Solution

```python
def get_city(user):
    if not isinstance(user, dict):
        return "invalid user"
    if "address" not in user:
        return "address missing"
    try:
        return user["address"]["city"]
    except KeyError:
        return "city missing"
```

### Tests

```python
print(get_city("abc"))
print(get_city({}))
print(get_city({"address":{}}))
print(get_city({"address":{"city":"chennai"}}))
```

### Rule

Validate outer structure first.

---

# 🧪 Exercise 8: Division Error

### Problem

```python
def calculate_average(total, count):
    return total / count
```

### Solution

```python
def calculate_average(total, count):
    if count == 0:
        return "cannot divide by zero"
    return total / count
```

### Tests

```python
print(calculate_average(10,0))
print(calculate_average(10,2))
```

### Rule

ZeroDivisionError → prevent with `if`

---

# 🧪 Exercise 9: Unexpected Input (Type + Key)

### Problem

```python
def get_role(user):
    return user["role"]
```

### Solution

```python
def get_role(user):
    if isinstance(user, str):
        return "invalid user"
    try:
        return user["role"]
    except KeyError:
        return "role not found"
```

### Tests

```python
print(get_role("abc"))
print(get_role({}))
print(get_role({"role":"admin"}))
```

### Rule

Wrong input type → validation
Missing key → exception

---

# 🧪 Exercise 10: FULL BACKEND SCENARIO ⭐

### Problem

```python
def process_user(user):
    return {
        "name": user["name"],
        "email": user["email"],
        "age": int(user["age"])
    }
```

### Solution

```python
def process_user(user):
    if not isinstance(user, dict):
        return "invalid user"
    if "name" not in user or "email" not in user:
        return "required field missing"
    try:
        age = int(user["age"])
    except (KeyError, ValueError):
        return "invalid age"
    return {
        "name": user["name"],
        "email": user["email"],
        "age": age
    }
```

### Tests

```python
print(process_user("abc"))
print(process_user({"name":"a"}))
print(process_user({"name":"a","email":"b","age":"x"}))
print(process_user({"name":"a","email":"b","age":"20"}))
```

### Rule

Real backend = validation + controlled exceptions

---

# 🔐 FINAL BACKEND TRUTH (IMPORTANT)

If you can:
• Identify what can go wrong
• Decide `if` vs `try/except`
• Return safe messages

👉 **You are backend-ready**
👉 Flask will feel EASY now

---

If you want next:
1️⃣ Convert these into Flask APIs
2️⃣ Get interview-style backend error questions
3️⃣ Build mini backend project safely

Just say **1 / 2 / 3**

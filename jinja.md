

## ✅ Correct full example (SAFE & CLEAN)

```bash
source venv/bin/activate
export FLASK_APP=flask2.py
export FLASK_DEBUG=1
flask run
```

Perfect question 👍
Here is **Jinja for backend developers ONLY** — nothing extra, nothing fancy.

You’ll see that Jinja is actually **very small**.

---

# 🧩 Jinja — **ONLY what you need**

> Goal:
> Connect Flask (Python) ↔ HTML
> Show data, forms, and errors

---

## 1️⃣ `{{ ... }}` → print something

Used to **display data** from Flask.

```jinja
{{ username }}
{{ form.email }}
```

Flask:

```python
return render_template("page.html", username="Vignesh")
```

Output:

```html
Vignesh
```

---

## 2️⃣ `{% ... %}` → logic (no output)

Used for **conditions, loops, structure**.

---

## 3️⃣ `{% if %}` → conditions

```jinja
{% if current_user.is_authenticated %}
    <a href="/logout">Logout</a>
{% else %}
    <a href="/login">Login</a>
{% endif %}
```

Used for:

* Showing errors
* Showing login/logout
* Optional content

---

## 4️⃣ `{% for %}` → loops

```jinja
{% for error in form.email.errors %}
    <p>{{ error }}</p>
{% endfor %}
```

Used for:

* Error messages
* Lists
* Repeating elements

---

## 5️⃣ `{% extends %}` → base template

```jinja
{% extends "layout.html" %}
```

Means:

> “Use layout.html as base”

Avoids repeating HTML.

---

## 6️⃣ `{% block %}` → placeholder

In `layout.html`:

```html
{% block content %}{% endblock %}
```

In page:

```jinja
{% block content %}
    <h1>Login</h1>
{% endblock %}
```

---

## 7️⃣ `url_for()` → build URLs safely

```jinja
<a href="{{ url_for('login') }}">Login</a>
```

Maps to:

```python
@app.route("/login")
def login():
```

No hardcoded URLs.

---

## 8️⃣ Flask-WTF helpers (VERY IMPORTANT)

### `form.hidden_tag()`

```jinja
{{ form.hidden_tag() }}
```

Adds:

* CSRF token
* Hidden fields

Mandatory for POST forms.

---

### Field rendering

```jinja
{{ form.email }}
{{ form.password }}
```

WTForms generates `<input>` automatically.

---

## 9️⃣ That’s it. Seriously.

You do **NOT** need:
❌ Macros
❌ Filters
❌ Template inheritance tricks
❌ Advanced syntax

---

## 🧠 Mental model (remember forever)

> **Jinja is just Python logic inside HTML.**

---

## 🧪 Minimal example (complete)

### Flask

```python
@app.route("/login", methods=["GET", "POST"])
def login():
    form = LoginForm()
    return render_template("login.html", form=form)
```

### Jinja

```jinja
<form method="POST">
    {{ form.hidden_tag() }}
    {{ form.email }}
    {{ form.password }}
    {{ form.submit }}
</form>
```

That’s a working page.

---

## ✅ Final checklist (Jinja mastery)

You now know:
✔️ Print values
✔️ Use if/else
✔️ Loop
✔️ Extend layout
✔️ Build URLs
✔️ Show form fields

That’s **100% enough** for backend Flask work.

---

If you want next, I can:

* Give **Jinja practice exercises**
* Show **common Jinja mistakes**
* Teach **conditional navbar**
* Combine **HTML + Jinja + FlaskForm**

Just tell me 👍


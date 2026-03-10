## Django Web Application Demonstration

### Assignment README

## Student Information

**Name:** Chessmore Chiremba
**Registration Number:** R2421698
**Programme:** HENELENG (Electrical and Electronics Engineering)

---

# Project Title

**Django Todo Web Application**

---

# Project Overview

This project demonstrates the development of a basic web application using the **Django web framework**. The purpose of the assignment is to illustrate how Django integrates the major components of web development, including routing, templates, models, and database interaction.

The application created is a **simple Todo List system** that allows users to add tasks, view tasks, and mark tasks as completed. The project highlights the implementation of Django's **Model–View–Template (MVT)** architecture.

---

# Objectives

The objectives of this assignment are:

* To understand the structure of a Django project.
* To demonstrate the creation of a Django application within a project.
* To implement **models** for database storage.
* To develop **views** that handle user requests.
* To render dynamic web pages using **templates (Jinja-style Django templating)**.
* To connect URLs to views.
* To use the Django **admin interface** for managing database entries.

---

# Technologies Used

| Technology                                 | Purpose                      |
| ------------------------------------------ | ---------------------------- |
| Python                                     | Backend programming language |
| Django                                     | Web development framework    |
| HTML                                       | Frontend structure           |
| Django Template Engine (Jinja-like syntax) | Dynamic page rendering       |
| SQLite                                     | Database used by Django      |
| Visual Studio Code                         | Development environment      |

---

# Project Structure

```
django_todo_project/
│
├── manage.py
├── db.sqlite3
│
├── project/
│   ├── settings.py
│   ├── urls.py
│   └── asgi.py
│
├── todo/
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── admin.py
│   └── migrations/
│
└── templates/
    └── home.html
```

---

# Key Components

## 1. Models

Models define the structure of the database.

Example model used in the application:

```python
from django.db import models

class Task(models.Model):
    title = models.CharField(max_length=200)
    completed = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

This model stores information about tasks including the task name, completion status, and creation date.

---

# 2. Views

Views handle user requests and return responses.

Example view:

```python
from django.shortcuts import render
from .models import Task

def home(request):
    tasks = Task.objects.all()
    return render(request, "home.html", {"tasks": tasks})
```

The view retrieves all tasks from the database and sends them to the template.

---

# 3. Templates

Templates are used to generate dynamic HTML pages.

Example template:

```html
<h1>Todo List</h1>

<ul>
{% for task in tasks %}
<li>
{{ task.title }}
{% if task.completed %}
✔ Completed
{% endif %}
</li>
{% endfor %}
</ul>
```

The template uses **Jinja-style Django template syntax** to loop through tasks and display them.

---

# 4. URL Routing

URL routing connects web addresses to specific views.

Example:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.home, name="home"),
]
```

This configuration directs the homepage URL to the `home` view.

---

# 5. Django Admin Panel

The Django admin interface allows administrators to manage database content.

The model is registered in `admin.py`:

```python
from django.contrib import admin
from .models import Task

admin.site.register(Task)
```

This allows tasks to be created, edited, or deleted through the admin dashboard.

---

# Running the Project

### 1. Install Django

```bash
pip install django
```

### 2. Run migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 3. Start the development server

```bash
python manage.py runserver
```

### 4. Access the application

Open a browser and go to:

```
http://127.0.0.1:8000
```

---

# Expected Output

The web application displays a list of tasks stored in the database and allows tasks to be managed through the Django admin panel.

---

# Conclusion

This assignment demonstrates how Django simplifies web application development by integrating database management, server-side logic, and frontend rendering. Through the implementation of models, views, templates, and URL routing, the project illustrates the core concepts of Django's MVT architecture.

The project provides a foundational understanding of building dynamic web applications using Python and Django.

---

# Author

**Chessmore Chiremba**
University of Zimbabwe
Electrical and Electronics Engineering Programme

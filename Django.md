# DJANGO TECHNICAL PAPER

## SETTINGS.PY
### 1. What is a Secret Key?
- The Secret Key in Django is a unique, randomly generated string that Django uses for cryptographic security operations. It helps Django make sure that data has not been tampered with and that requests are coming from trusted sources.

- This key is used for signing session cookies, generating password reset tokens, protecting CSRF tokens, and securing authentication-related data. If someone gets access to the secret key, they can forge cookies or generate fake tokens, which is a serious security risk.

- Because of this, the secret key should never be shared or committed to public repositories. In production environments, it is usually stored in environment variables instead of directly in settings.py.

### 2. What are the default Django apps inside it? Are there more?
- Django provides several default built-in apps that are enabled in the INSTALLED_APPS setting. These apps give Django many powerful features without writing extra code.

- Some important default apps include the admin app for managing data, the authentication app for handling users and passwords, the sessions app for storing user sessions, and the static files app for serving CSS and JavaScript files. These apps work together to provide the basic functionality required by most web applications.

- Yes, Django also provides additional optional contrib apps, and developers can create their own custom apps based on project needs. Django follows a modular design, so apps can be added or removed easily.

### 3. What is Middleware?
- Middleware in Django is a request–response processing layer that sits between the web server and the Django view. Every HTTP request passes through middleware before reaching the view, and every response passes through middleware before going back to the browser.

- Middleware is mainly used for performing tasks that need to run on every request, such as authentication checks, security validations, session handling, and request logging. It helps keep views clean and focused on business logic.

- Django executes middleware in the order defined in the MIDDLEWARE list, which makes the sequence of execution very important.

### 4. What are the different kinds of Middlewar?
- Django includes several middleware classes that focus on security and request handling. These middleware components automatically protect applications from common attacks.

- Security middleware adds important HTTP headers to improve browser security. CSRF middleware checks for valid CSRF tokens in POST requests. Authentication middleware attaches the logged-in user to every request. Clickjacking middleware prevents the site from being embedded inside iframes.

- Together, these middleware classes provide a strong first line of defense for Django applications.

### 5. What is CSRF?
- CSRF (Cross-Site Request Forgery) is an attack where a malicious website forces a logged-in user’s browser to send an unwanted request to another website. This can result in actions being performed without the user’s knowledge.

Django protects against CSRF by using CSRF tokens, which are unique and secret values added to HTML forms. When a form is submitted, Django verifies this token before processing the request.

If the CSRF token is missing or incorrect, Django automatically rejects the request.

### 6. What is XSS?
- XSS (Cross-Site Scripting) occurs when attackers inject malicious JavaScript code into a website. When other users load that page, the script runs in their browser and can steal data or perform actions on their behalf.

- Django prevents XSS attacks by auto-escaping user input in templates. This ensures that any HTML or JavaScript entered by users is displayed as plain text instead of being executed.

- Only when developers explicitly disable escaping does the risk of XSS increase.

### 7. What is Clickjacking?

Clickjacking is an attack where a website is loaded inside an invisible or deceptive iframe on another site. Users are tricked into clicking buttons or links without realizing what they are interacting with.

Django protects against clickjacking by sending the X-Frame-Options header, which prevents the site from being embedded inside iframes. This protection is enabled by default through middleware.

This ensures that users interact with the site directly and safely.

### 8. Any other middleware that is there?

Apart from security middleware, Django provides middleware for common tasks such as URL normalization, localization, message handling, and error reporting. These middleware components improve user experience and application reliability.

Django also allows developers to create custom middleware for project-specific needs, such as request timing, custom logging, or API request validation.

Middleware makes Django applications more modular and easier to maintain.

### 9. What is WSGI?

WSGI (Web Server Gateway Interface) is a standard interface that allows Python web applications to communicate with web servers. It defines how requests are passed from the server to the application and how responses are returned.

In Django, the wsgi.py file acts as the entry point for production deployments. Web servers like Gunicorn or uWSGI use this interface to run Django applications.

WSGI makes Django portable and compatible with different web servers.

## Models.py
### 1. What is ondelete cascade?
- on_delete = CASCADE is used in Django ForeignKey relationships to define what should happen when the parent object is deleted.

- When CASCADE is used, all related child records are automatically deleted along with the parent record. This helps maintain database integrity by avoiding orphan records.

- Example:
```bash
class Author(models.Model):
    name = models.CharField(max_length=100)

class Book(models.Model):
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

### 2. What are Filds and Validators?

**Fields in Django Models**
- Fields define the type of data stored in database columns. Each field maps to a column in the database table.
- Some commonly used fields are:
1. CharField → Stores short text
2. TextField → Stores long text
3. IntegerField → Stores integers
4. FloatField → Stores decimal numbers
5. BooleanField → Stores True or False
6. DateField → Stores date
7. DateTimeField → Stores date and time
8. EmailField → Stores email addresses
9. FileField / ImageField → Stores files and images
10. ForeignKey → Creates relationships between tables

**Validators in Django**
- Validators are used to validate data before saving it to the database. They ensure that only valid data is stored.
- Common validators include:
1. max_length → Limits text length
2. MinValueValidator → Sets minimum value
3. MaxValueValidator → Sets maximum value
4. EmailValidator → Validates email format
5. RegexValidator → Validates using regular expressions
6. blank=True → Allows empty value in forms
7. null=True → Allows NULL in database

```bash
from django.core.validators import MinValueValidator

age = models.IntegerField(validators=[MinValueValidator(18))
```

### 3. What is the difference between Python modules and Python Classes
**Python Module**

- A module is a file that contains Python code such as variables, functions, and classes. It helps in organizing code into separate files.
- A module is created using a .py file
- It is imported using the import keyword
- Used to group related functionality
- Example:
```bash
import math
```
- A module is mainly used for code organization and reuse.

**Python Class**

- A class is a blueprint for creating objects. It defines properties (variables) and behaviors (methods).
- Classes are defined using the class keyword
- Objects are created from classes
- Used for object-oriented programming
- Example:
```bash
class Student:
    name = "Jahnavi"
```
- A class is mainly used for creating objects and modeling real-world entities.

## Django ORM

### 1. What are ORM queries in Django shell
- Django Shell is an interactive Python shell that allows developers to test ORM queries, inspect data, and debug database operations.
- You can open the Django shell using:
```bash
python manage.py shell
```
- Inside the shell, you can import models and perform queries like:
1. Fetching all records
2. Filtering data
3. Creating or deleting records
- This is very useful for quick testing without running the server or writing views.

### 2. How to turn ORM to SQL in Django Shell

- Django allows you to see the actual SQL query generated by ORM. This helps in understanding how ORM works internally and in debugging performance issues.

- By converting ORM queries to SQL, developers can analyze query efficiency and database behavior. Django automatically converts Python ORM code into optimized SQL statements before sending them to the database.

- This feature is mainly used for learning, debugging, and performance optimization.

### 3. What are Aggregations?
- Aggregations are ORM operations that calculate a single summary value from multiple rows in a database table.
- They are commonly used to compute values like:
1. Total count
2. Average
3. Minimum or maximum
4. Sum of values
- Aggregations return one result, not a queryset. They are useful for reports, dashboards, and analytics where summarized data is needed.

### 4. What are Annotations?

- Annotations are used to add calculated values to each object in a queryset. Unlike aggregations, annotations return results per row, not a single value.

- With annotations, Django adds an extra field to every object based on calculations such as count or sum of related data. This allows developers to access computed values as if they were normal model fields.

- Annotations are useful when each record needs additional computed information.

### 5. What is a Migration File? Why is it needed?

- A migration file is a record of changes made to Django models. It tells Django how to update the database schema when models change.

- Migration files are needed because databases do not automatically understand changes in Python models. Whenever fields are added, removed, or modified, migrations ensure that the database structure stays in sync with the models.

- They also help track database changes over time and allow consistent updates across different environments.

### 6. What are SQL Transactions?
- A SQL transaction is a sequence of database operations that are treated as one single unit of work. Either all operations succeed, or none of them are applied.
- Transactions follow the ACID properties:
1. Atomicity
2. Consistency
3. Isolation
4. Durability
- They are used to maintain data integrity, especially in situations involving multiple related database operations such as money transfers or bulk updates.

### 7. What are Atomic Transactions?
- Atomic transactions ensure that a block of database operations is fully completed or fully rolled back if an error occurs.
- In Django, atomic transactions guarantee that partial changes are not saved to the database when an exception happens. This helps prevent inconsistent or corrupted data.
- Atomic transactions are especially important in applications dealing with critical data where failure in one operation should cancel all related operations.

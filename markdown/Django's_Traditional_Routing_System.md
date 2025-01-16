### **Tutorial: Django's Traditional Routing System**

Django's **traditional routing system** is a core mechanism that maps URLs to views. It relies on defining URL patterns in `urls.py` files using functions like `path()` and `re_path()`. Understanding this system is essential for managing how your application handles HTTP requests and delivers responses.

----------

### **Key Components of Django's Traditional Routing System**

1.  **URL Dispatcher**:
    
    -   Matches incoming HTTP requests to the appropriate view function based on defined patterns.
    -   Operates through a sequence of `urlpatterns` in `urls.py`.
2.  **`urls.py` File**:
    
    -   The central place for defining URL-to-view mappings.
    -   Uses Django’s `path()` for straightforward patterns and `re_path()` for complex regular expression-based patterns.
3.  **Views**:
    
    -   Functions or class-based handlers that process requests and generate responses.
    -   Associated with specific URL patterns.

----------

### **Step-by-Step Guide to Django's Traditional Routing System**

#### **1. Defining URL Patterns in `urls.py`**

The main `urls.py` file is found in the project directory, alongside `settings.py` and other core files.

Example:

```python
# mysite/urls.py
from django.contrib import admin
from django.urls import path
from myapp import views  # Import your app's views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.home, name='home'),  # Root URL
    path('about/', views.about, name='about'),  # About page
]

```

----------

#### **2. Connecting Views to URL Patterns**

Create views to handle requests for specific URLs.

Example:

```python
# myapp/views.py
from django.http import HttpResponse

def home(request):
    return HttpResponse("Welcome to the Home Page!")

def about(request):
    return HttpResponse("This is the About Page!")

```

----------

#### **3. Using Dynamic Parameters in URLs**

Django's traditional system allows capturing URL parameters for dynamic content handling.

Example:

```python
# mysite/urls.py
urlpatterns = [
    path('article/<int:id>/', views.article_detail, name='article_detail'),
]

# myapp/views.py
def article_detail(request, id):
    return HttpResponse(f"You're viewing article {id}.")

```

-   `<int:id>` captures an integer and passes it to the `article_detail` view as the `id` parameter.

----------

#### **4. Named URL Patterns**

Named patterns make it easier to reference URLs across your application.

Example:

```python
# mysite/urls.py
urlpatterns = [
    path('blog/', views.blog, name='blog'),
]

```

-   Reference in templates: `{% url 'blog' %}`
-   Reference in views: `reverse('blog')`

----------

#### **5. Organizing URLs with `include()`**

For larger applications, you can split URL configurations across multiple `urls.py` files using `include()`.

Example:

```python
# mysite/urls.py
from django.urls import include

urlpatterns = [
    path('app1/', include('app1.urls')),  # Include app1's URL config
    path('app2/', include('app2.urls')),  # Include app2's URL config
]

```

Each app will have its own `urls.py` file:

```python
# app1/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]

```

----------

#### **6. Using `re_path` for Complex Patterns**

For more advanced URL matching, use `re_path` with regular expressions.

Example:

```python
from django.urls import re_path

urlpatterns = [
    re_path(r'^articles/(?P<year>[0-9]{4})/$', views.year_archive),
]

```

-   This matches URLs like `/articles/2024/`.

----------

#### **7. Customizing 404 Error Pages**

If no URL matches the patterns, Django raises a `404 Page Not Found` error. You can define a custom handler for this.

Example:

```python
# mysite/views.py
from django.http import HttpResponseNotFound

def custom_404_view(request, exception):
    return HttpResponseNotFound("Custom 404 Page Not Found")

# Add this in settings.py
HANDLER404 = 'mysite.views.custom_404_view'

```

----------

#### **8. Class-Based Views in Traditional Routing**

Class-based views work seamlessly with Django's traditional routing system.

Example:

```python
from django.urls import path
from django.views.generic import TemplateView

urlpatterns = [
    path('about/', TemplateView.as_view(template_name='about.html')),
]

```

----------

### **Summary of Django's Traditional Routing System**

1.  **Main Features**:
    
    -   URL patterns defined in `urls.py` using `path()` or `re_path()`.
    -   Straightforward mapping of URLs to views.
2.  **Advanced Usage**:
    
    -   Use `include()` to keep URL configurations modular and organized.
    -   Leverage dynamic URL parameters and regular expressions for flexibility.
3.  **Best Practices**:
    
    -   Keep `urls.py` files organized for better maintainability.
    -   Use named URLs for consistency across templates and views.
    -   Validate inputs passed via URL parameters to avoid errors.

Django’s **traditional routing system** remains a powerful, flexible way to control URL handling, enabling you to create dynamic and robust web applications.

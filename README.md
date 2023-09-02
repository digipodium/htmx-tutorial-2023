`Team digipodium presents`
---
# HTMX Tutorial

In this tutorial, we will explore HTMX, a library that allows you to enhance your web applications with interactive features without writing a lot of JavaScript code. HTMX is a great tool for developers who want to create dynamic web applications with minimal effort. We will cover the basics of HTMX, including its core concepts, attributes, actions, and even provide a Django example.

## Table of Contents

1. [Introduction to HTMX](#introduction-to-htmx)
2. [Getting Started](#getting-started)
3. [Attributes](#attributes)
   - [hx-get](#hx-get)
   - [hx-post](#hx-post)
   - [hx-put](#hx-put)
   - [hx-delete](#hx-delete)
4. [Actions](#actions)
   - [hx-trigger](#hx-trigger)
   - [hx-confirm](#hx-confirm)
   - [hx-select](#hx-select)
5. [Django Example](#django-example)

## 1. Introduction to HTMX

HTMX is a library that enables you to create dynamic and interactive web applications with ease. It allows you to update parts of a web page without having to write extensive JavaScript code. HTMX relies on HTML attributes and actions to handle interactions and make requests to the server, making it a powerful tool for enhancing user experiences.

## 2. Getting Started

To get started with HTMX, you need to include the HTMX script in your HTML file. You can download it from the [official HTMX website](https://htmx.org/) or include it from a content delivery network (CDN):

```html
<script src="https://unpkg.com/htmx.org@latest/dist/htmx.js"></script>
```

Once you've included the HTMX script, you can start adding HTMX attributes and actions to your HTML elements.

## 3. Attributes

HTMX attributes are used to define the behavior of HTML elements. These attributes are prefixed with "hx-" and provide instructions to HTMX on how to handle interactions.

### a. hx-get

The `hx-get` attribute is used to fetch content from the server and replace the content of the current element with the response. Here's an example:

```html
<button hx-get="/api/data" hx-target="#result">Fetch Data</button>
<div id="result">Data will be displayed here.</div>
```

In this example, when the "Fetch Data" button is clicked, HTMX makes a GET request to `/api/data` and updates the content of the `#result` div with the response.

### b. hx-post

The `hx-post` attribute is used to send data to the server using a POST request. It can be combined with other attributes like `hx-target` to specify where the response should be placed. Here's an example:

```html
<form hx-post="/submit" hx-target="#result">
    <input type="text" name="username" placeholder="Enter your username">
    <button type="submit">Submit</button>
</form>
<div id="result">Response will be displayed here.</div>
```

In this example, when the form is submitted, HTMX sends a POST request to `/submit` with the form data and updates the content of the `#result` div with the response.

### c. hx-put

The `hx-put` attribute is similar to `hx-post` but sends a PUT request to the server. It's used for updating existing resources. Here's an example:

```html
<button hx-put="/update" hx-trigger="click">Update Data</button>
```

In this example, when the "Update Data" button is clicked, HTMX sends a PUT request to `/update`.

### d. hx-delete

The `hx-delete` attribute sends a DELETE request to the server to delete a resource. Here's an example:

```html
<button hx-delete="/delete" hx-confirm="Are you sure?" hx-target="#result">Delete Data</button>
```

In this example, when the "Delete Data" button is clicked, HTMX sends a DELETE request to `/delete` after confirming with the user.

## 4. Actions

Actions in HTMX allow you to define behavior in response to events.

### a. hx-trigger

The `hx-trigger` attribute specifies the event that triggers an action. It can be used in conjunction with other attributes like `hx-get` or `hx-post`. Example:

```html
<button hx-get="/data" hx-trigger="click">Fetch Data on Click</button>
```

In this example, the data is fetched when the button is clicked.

### b. hx-confirm

The `hx-confirm` attribute is used to show a confirmation dialog before an action is executed. Example:

```html
<button hx-post="/submit" hx-confirm="Are you sure you want to submit?" hx-target="#result">Submit</button>
```

This button will display a confirmation dialog before submitting the form.

### c. hx-select

The `hx-select` attribute allows you to specify elements to be updated when an action is triggered. Example:

```html
<button hx-get="/data" hx-select="#result">Fetch Data</button>
<div id="result">Data will be displayed here.</div>
```

In this example, when the button is clicked, the content of the `#result` div will be updated.

## 5. Django Example

Now, let's see a simple Django example using HTMX. We'll create a counter that increments when a button is clicked.

```html
<!-- Django Template -->
<button hx-post="{% url 'increment_counter' %}" hx-target="#counter">{{ counter }}</button>
<div id="counter">{{ counter }}</div>
```

In this Django template, we have a button that sends a POST request to the `increment_counter` URL and updates the content of the `#counter` div with the counter value.

In your Django views, you can handle the POST request and increment the counter value:

```python
# views.py
from django.http import JsonResponse

counter = 0

def increment_counter(request):
    global counter
    counter += 1
    return JsonResponse({'counter': counter})
```

This example demonstrates how to use HTMX with Django to create a dynamic counter without writing complex JavaScript code.

Congratulations! You've learned the basics of HTMX and how to use it to enhance your web applications with minimal effort. HTMX's attributes and actions make it a powerful tool for creating interactive web pages.

official documentation -> [htmx website](https://htmx.org/)

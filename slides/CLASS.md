## MelbDjango School

### Lesson Seven — APIs

---

## WIFI

Common Code / cc&20!4@

---

Thanks for doing the assignment!

---

# Building JSON APIs with Django

---

## What does "interface" mean?

---

## What does "interface" mean?

<dl>
<dt>interface (plural interfaces)</dt>
<dd>The point of interconnection between entities.</dd>
</dl>

---

## What is an API?

- Application Programming Interface
- An interface defined for your application that you can use to access data
  - Or let others use!
- We're going to build a RESTful API

---

## Why we bulid APIs

Old sites:
- Server rendered content.
- Every user click reloads the page.
- A little JS (form validation, animations, etc).

Modern sites:
- Heavy JS usage.
- Browser rendered content.
- Dynamically update the current page 
- Actions are performed "in the background".

---

## What is JSON?

- Javascript Object Notation
- `content-type: application/json`
- Can be natively read by Javascript (handy for the web!)
- There are libraries for handling it in most languages

---

## What is JSON?

```javascript
{
  "id": 1,
  "title": "MelbDjango School - Lesson Seven",
  "teacher": "@sesh"
  "classes": [
    "lesson 1",
    "lesson 4",
    "lesson 9"
  ]
}
```

---

## Why JSON?

Why not XML, CSV, etc?

- We only have a single language (Javascript) available in the browser.
- JSON is "free" in the browser.
- XML is a document markup language, not a data format.
- XML is ugly.

---

## What does `RESTful` mean?

`Representational state transfer`

A design pattern for building scalable web services.

- Designed for HTTP
- Relies on HTTP verb semantics (GET, POST, etc)
- Relies on URL/URIs
- Uses HTTP status codes

---

## What does `RESTful` mean?

- Records are addressable at URLs
- To create/read/update/delete we use POST/GET/PUT/DELETE respectively.
- Can reference other records by URL.

---

## Benefits of REST

- Stateless
- Cacheable
- Layered

---

## What's out there?

- DRF
- django-nap
- TastyPie
- restless

---

## Building From Scratch

---

## What does Django bring?

`JsonResponse`

- New in Django 1.7
- Subclass of HTTPResponse
- Accepts a dict of data
- Returns JSON encoded string

Note: Why dict?  safe=False

---

## Overview

- List views
  - Get all records
  - POST new records
- Detail views
  - Get a single record
  - Update a single record
  - Delete a single record

---

## A Mixin

```
from django.http import JsonResponse

class JsonResponseMixin(object):
    '''
    A mixin mostly compatible with TemplateResponseMixin
    '''

    response_class = JsonResponse
    content_type = 'application/json'

    def render_to_response(self, context, **response_kwargs):
        response_kwargs.setdefault('content_type', self.content_type)
        return self.response_class(content, **response_kwargs)
```

[see](https://github.com/django/django/blob/master/django/views/generic/base.py#L112)

---

## List view

    from django.views.generic import ListView

    from .models import Entry
    from .utils import JsonResponseMixin


    class EntryListView(JsonResponseMixin, ListView):
        model = Entry


---

## Is that it??

- Sadly, no.

---

## Oh...

We need to "reduce" our Python objects to simple dicts of JSON types.

This is generally called "serialising".

---

## Serialisers

- Convert Python objects to simple types.
- Convery data from requests back to Python objects.

`django.core.serialisers`

- Basic
- Used for fixtures, dumpdata, loaddata
- Inflexible

---

## Using forms in our API


---

![](https://raw.githubusercontent.com/CapnKernel/melbdjango-assignment/master/guestbook/static/img/agbdunderconstruction7.gif)




---

## We're Almost Done!

- Two more classes:
  - Deploying your Django App
  - Some more advanced Django topics
  - Demo Day!

- MelbDjango School 201 will launch soon!

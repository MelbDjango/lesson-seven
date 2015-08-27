## MelbDjango School

### Lesson Seven — Authentication & APIs

---

## WIFI

Common Code / cc&20!4@

---

Thanks for doing the assignment!

---

django.contrib.auth

- Installed by default
- Add `django.contrib.auth` to your installed apps if it's not
- You need to migrate to create the models in the database

---

django.contrib.auth.models.User

---

You can create your own user model

---

Creating users

---

Logging a user in

- authenticate(username="", password="")
- login(request, user)

- You _must_ call authenticate first

---

Logging a user out

- A whole heap simpler, since Django just clears the session data.
- logout(request)

---

Checking if the user is logged in

- request.user.is_authenticated()
- from django.contrib.auth.decorators.login_required

---

A note about changing password

- user set_password()


---

Django provides views to do most of these tasks

---

Creating Foreign Keys to Users



---

# Building JSON APIs with Django

---

## What is an API?

- Application Programming Interface
- An interface defined for your application that you can use to access data
  - Or let others use!
- We're going to build a RESTful API

---

## Why we bulid APIs

- Websites use APIs to create more dynamic front ends
  - Instead of rendering templates on the server, you make calls to the API with javascript

- A lot of websites (Github, Twitter, Instagram, Google, etc.) define APIs that let developers access data from them
  - Normally there are `Application Keys` the identify the user for security reasons
  - There are almost always rules around what you can and can't do with the data

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
}
```

---

## Why JSON?

- Why not XML, CSV, etc?
  - We only have a single language (Javascript) available in the browser
  - XML is ugly

---

## What's out there?

- DRF
- django-nap
- tastypie
- restless

---

## Building From Scratch

---

## JSONResponse

- New in Django 1.7
- Just like HTTPResponse, but it takes a dictionary

---

safe==False

Well, that sounds kinda bad.

---

Building a simple API for our Entries

---

What about creating objects?
POST

---

Using forms in our API

---

Good REST API Design

- Return the right status code






---

## We're Almost Done!

- Two more classes:
  - Deploying your Django App
  - Some more advanced Django topics
  - Demo Day!

- MelbDjango School 201 will launch soon!

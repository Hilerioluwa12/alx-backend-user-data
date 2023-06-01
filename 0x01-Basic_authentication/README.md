0x01. Basic authentication

In this project, you will learn what the authentication process means and implement a Basic Authentication on a simple API.

In the industry, you should not implement your own Basic authentication system and use a module or framework that doing it for you (like in Python-Flask: Flask-HTTPAuth). Here, for the learning purpose, we will walk through each step of this mechanism to understand it by doing.


What authentication means
What Base64 is
How to encode a string in Base64
What Basic authentication means
How to send the Authorization header


Download and start your project from this archive.zip

In this archive, you will find a simple API with one model: User. Storage of these users is done via a serialization/deserialization in files.

Setup and start server
bob@dylan:~$ pip3 install -r requirements.txt
...
bob@dylan:~$
bob@dylan:~$ API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
 * Serving Flask app "app" (lazy loading)
...
bob@dylan:~$
Use the API (in another tab or in your browser)


1. Error handler: Unauthorized
mandatory
What the HTTP status code for a request unauthorized? 401 of course!

Edit api/v1/app.py:

Add a new error handler for this status code, the response must be:
a JSON: {"error": "Unauthorized"}
status code 401
you must use jsonify from Flask
For testing this new error handler, add a new endpoint in api/v1/views/index.py:

Route: GET /api/v1/unauthorized
This endpoint must raise a 401 error by using abort - Custom Error Pages
By calling abort(401), the error handler for 401 will be executed.

In the first terminal:

bob@dylan:~$ API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
 * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
...

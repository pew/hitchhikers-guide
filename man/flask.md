# flask

a cool python web framework.

# tips and tricks

some pitfalls I run into ~all the time~ from time to time.

## gunicorn / multiple processes and SECRET

if you're using gunicorn to use your app with multiple threads AND you're using something like `os.urandom()` to set the flask `SECRET` key, you'll end up with a mess, since every thread/process has it's own key this way.

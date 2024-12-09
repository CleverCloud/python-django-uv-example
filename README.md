# Django with Uvicorn deployed from `uv` on Clever Cloud

You'll need a Clever Cloud account and [Clever Tools](https://github.com/CleverCloud/clever-tools/) to deploy this application, using our Python image [now including](https://developers.clever-cloud.com/changelog/2024-10-01-python-image-changes/) `uv`.

## Clone this repository and configure a Clever Cloud application

```bash
git clone https://github.com/CleverCloud/python-django-uv-example.git
cd python-django-uv-example

clever create -t python
clever env set CC_RUN_COMMAND "uv run -- uvicorn --host 0.0.0.0 --port 9000 myDjango.asgi:application"
clever deploy && clever open
```

## How this app was created

To create the same app as this one on a machine with `uv` installed, you can use the following commands:

```bash
uv init myDjango --no-readme                    # Create a new uv project
cd myDjango && rm hello.py                      # Enters the project and clean it
uv add django uvicorn                           # Adds Django and Uvicorn to dependencies
uv run django-admin startproject myDjango .     # Creates the Django project in the current directory
```

Edit `myDjango/settings.py` to add `ALLOWED_HOSTS` (`*` in this example), change secret key, etc. Commit changes to the local git repository, and then you can create and deploy this app on Clever Cloud as mentioned above.

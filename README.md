# Getting Started: Setup Python and Django (Windows)
## Create Python virtual environment
This is used to separate our project environment from the system installed Python envrionment.   
This protects the system installed libraries from potential changes made by installing/removing packages for our app.   

1. Create a new virtual environment:   
`py -m venv .venv`
2. Start the new virtual environment (Windows):   
`.venv\Scripts\Activate.ps1`    

## Install Django (and other dependencies)
- Install the Django framework using pip:   
`py -m pip install Django`
- Install tweaks to allow for easy customization of form CSS.
`py -m pip install django-widget-tweaks`   

## Create Requirements File
- Lists all the dependencies necessary for a project, often including version numbers.
- Used to create a consistent environment using `pip install -r requirements.txt`.
`pip freeze > requirements.txt`   

## Create and Start Project
1. Create new Django project in current directory (replace 'my_project' with project name).   
`django-admin startproject my_project .`   
2. Start the server on desired port.     
`py manage.py runserver 8080`  

## Project Layout
```
my_project/
│
├── manage.py               # Django management script
├── README.md               # Readme file describing the project
├── requirements.txt        # Python required modules and dependencies
├── .gitignore              # Git ignore file (exclude files/dirs when commiting to git)
├── .venv                   # Python virtual environment
├── my_project/             # Main project folder
│   ├── __init__.py
│   ├── settings.py         # Or a settings/ folder with separate files (base.py, dev.py, prod.py)
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
│
├── apps/                   # Directory for all Django apps
│   ├── __init__.py         # Makes 'apps' a Python package
│   ├── app1/               # First Django app
│   │   ├── migrations/
│   │   ├── __init__.py
│   │   ├── admin.py
│   │   ├── apps.py
│   │   ├── models.py
│   │   ├── tests.py
│   │   ├── views.py
│   │   ├── urls.py         # App-specific URL configuration
│   │   ├── static/         # App-specific static files
│   │   └── templates/      # App-specific templates
│   └── app2/               # Another Django app
│       ├── migrations/
│       ├── __init__.py
│       ├── admin.py
│       ├── apps.py
│       ├── models.py
│       ├── tests.py
│       ├── views.py
│       ├── urls.py
│       ├── static/
│       └── templates/
│
├── templates/              # Global templates
│   ├── base.html
│   └── ...
│
└── static/                 # Global static files (e.g., CSS, JavaScript, images)
    ├── css/
    ├── js/
    └── images/
```


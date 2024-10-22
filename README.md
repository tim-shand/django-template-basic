# Getting Started: Setup Python and Django (Windows)
## Create Python Virtual Environment
This is used to separate our project environment from the system installed Python environment.   
This protects the system installed libraries from potential changes made by installing/removing packages.   
- Create a new virtual environment named ".venv":   
`py -m venv .venv`
- Start the new virtual environment:   
`.venv\Scripts\Activate.ps1`    

## Install Django (and other dependencies)
- Install the Django framework inside the Python virtual environment using pip:   
`py -m pip install Django`
- Install tweaks to allow for easy customization of form CSS.   
`py -m pip install django-widget-tweaks`   

## Create Requirements File
- Lists all the dependencies necessary for a project, including version numbers.
- Used to create a consistent environment when using `pip install -r requirements.txt`.   
`pip freeze > requirements.txt`   

## Create New Project
- Create new Django project in current directory (replace 'my_project' with project name).   
`django-admin startproject my_project .`   

- Make initial database migrations. 
- Required to allow us to create a super user admin account.   
`py manage.py makemigrations`   
`py manage.py migrate`   

- Create super user account.   
`py manage.py createsuperuser`   
```
Username (leave blank to use 'root'): webadmin
Email address: [leave blank]
Password: 
Password (again): 
Superuser created successfully
```

## Run the Web Server
- Start the server on desired port.    
`py manage.py runserver 8080`  
- Main URL: http://127.0.0.1:8080/
- Admin URL: http://127.0.0.1:8080/admin/
- Use `CTRL + C` to stop the web server.

## Create Apps
- Create directory to contain all apps.   
`mkdir my_apps`   
- Create new Django apps (as required).   
`mkdir my_apps/blog`   
`py manage.py startapp blog ./my_apps/blog`   
`mkdir my_apps/users`   
`py manage.py startapp users ./my_apps/users`   

## Project Layout
```
root/
│
├── manage.py               # Django management script.
├── README.md               # Readme file describing the project.
├── requirements.txt        # Python required modules and dependencies.
├── .gitignore              # Git ignore file (exclude files/dirs when commiting to git).
├── .venv                   # Python virtual environment.
├── my_project/             # Main project/config folder.
│   ├── __init__.py
│   ├── settings.py         # Or a settings/ folder with separate files (base.py, dev.py, prod.py).
│   ├── urls.py             # Map URL requests to app functions.
│   ├── wsgi.py
│   └── asgi.py
│
├── my_apps/                # Directory for all Django apps.
│   ├── __init__.py         # Makes 'apps' a Python package.
│   ├── blog/               # First Django app (Blog).
│   │   ├── migrations/     # Records of database migrations, when model changes are made.
│   │   ├── __init__.py
│   │   ├── admin.py        # Register models in the admin interface.
│   │   ├── apps.py         # App specific configuration.
│   │   ├── models.py       # Database models, similar to defining the tables and datatypes.
│   │   ├── forms.py        # Form templates to use with HTML and models.
│   │   ├── tests.py
│   │   ├── views.py        # Functions to be executed when project URLs are requested.
│   │   ├── urls.py         # App-specific URL configuration.
│   │   └── templates/      # App-specific templates (HTML).
│   └── users/               # Second Django app (Users).
│       ├── migrations/
│       ├── __init__.py
│       ├── admin.py
│       ├── apps.py
│       ├── models.py
│       ├── tests.py
│       ├── views.py
│       ├── urls.py
│       └── templates/
│
├── templates/              # Global templates.
│   ├── base.html           # Used as base HTML template for other pages to built upon.
│   └── ...
│
└── static/                 # Global static files (CSS, JavaScript, images).
    ├── css/
    ├── js/
    └── images/
```

## Add to Github
- Ensure you have your '.gitignore' file populated before committing.
```
git init
git remote add origin https://github.com/[username]/[repo_name].git
git add .
git commit -m "Initial Commit."
git push -u origin main
```

## Run in Docker
### Overview
1. Create a Dockerfile with custom image instructions.
2. Add a .dockerignore file.
3. Build the image.
4. Create a docker-compose.yml file.
5. Spin up the container(s).

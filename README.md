# ed-example (Electron Django)
**Electron and django desktop application.**

When it comes to building a deployable standalone app for windows or mac using python, We python developers have comparatively less choices. The very first step is to choose a GUI kit for your python app. There are several GUI kits available for python, like PyQT, Tkinter, Kivy, WxPython etc. But all these are quite old and provide ancient looking GUIs. So To provide morden looking GUIs the only and most efficient choice we have is ElectronJs.

This project gives example boiler plate for electronjs in the frontend and django in the backend.

```
Requirements:
node: v18.17.1
python: 3.6.5
```

Backend aspect of project is in `python` directory.

Steps to verify and run the app.
1. Create a virtual env.
```
$ python3 -m venv ed-env
``` 
2. Install the packages.
```
(Django (3.2.23)
djangorestframework (3.14.0))

$ cd python
$ pip install -r requirements.txt
```
3. Verify and run the django server.
```
dir : python/EdExmple
python manage.py runserver
```
You should be able to see the django starter page on http://127.0.0.1:8000 

<img width="1010" alt="Screenshot 2023-11-24 at 2 15 37 PM" src="https://github.com/sandeepV2/ed-example/assets/52043035/6ada30d2-cc24-4fe8-8401-96a0e3e95ea9">


4. Great, If you are able to run the django server. Now lets look into starting the server via electron js.
Django server will be made to run as child process of electon js.
All you have to do is to provide right path of the executables.
```
in the src/index.js update the spawn call with appropriate files.

const startDjangoServer = () =>
{
    const djangoBackend = child_process.spawn(`python3`,
        ['<User_relative_path>/ed-example/python/edExample/manage.py', 'runserver', '--noreload']);

Note: this command may very as per platform
Example for windows:
const djangoBackend = spawn(`python\\edtwExampleEnv\\Scripts\\python.exe`,
        ['python\\edtwExample\\manage.py', 'runserver', '--noreload']);
```
5. Now you are ready to start complete app (frontend + backend)
```
Note : keep your python enviroment active.
$ npm run start
```
<img width="620" alt="Screenshot 2023-11-24 at 2 15 48 PM" src="https://github.com/sandeepV2/ed-example/assets/52043035/17c1e06a-930f-43aa-bab0-7ddf83ae4ef7">


This is just a development setup, how could you package it for prod env ?


Project is created using `create-electon-app` quite similar to `create-react-app`. 
```
$ npm install create-elecron-app -g
$ npm create-electon-app ed-example
```

References:
https://ivanyu2021.hashnode.dev/electron-django-desktop-app-integrate-javascript-and-python



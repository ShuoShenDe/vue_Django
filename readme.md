# This project is created for integrate vue and Django framework

## Step 1: Build Django Environment
```use pip
pip install Django
```
Then create an app

## Step 2: Build VUE Environment

```use npm
npm install -g @vue/cli @vue/cli-service-global
```
Then create a project
```use vue
vue init webpack my-project
```
Run it
```use npm
$ cd my-project
$ npm install
$ npm run dev
```
![vue reference](https://cli.vuejs.org/guide/)(https://www.runoob.com/vue2/vue-tutorial.html)


backend: an app of Django(package vueproject)
frontend: an vue project(package my-project)
Structure:
.
├── vueproject
│   ├── __init__.py
│   ├── tests.py
│   ├── views.py
│   ├── settings.py
│   └── urls.py
├── my-project
│   ├── README.md
│   ├── build
│   │   └── ....
│   ├── config
│   │   ├── dev.env.js
│   │   ├── index.js
│   │   ├── prod.env.js
│   │   └── test.env.js
│   ├── index.html
│   ├── package.json
│   ├── src
│   │   └── ...
│   ├── static
│   └── test
│       └── ...
├── manage.py


## Step 3: integrate vue and Django

Use webpack to package my-project

```use npm
cd my-project
npm install
npm run build
```
Then you will see a new folder(dist), which include index.html.

Back to Djnago project, and find urls.py(vueproject/urls.py)

```set new url
url(r'^$', TemplateView.as_view(template_name="index.html")),
```

Next, you should change the template search path of Django. Open settings.py(vueproject/settings.py), find TEMPLATES and STATICFILES_DIRS

```set TEMPLATES
TEMPLATES = [
    {
        ....
        'DIRS': ['my-project/dist'],
        ....
    },
]
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "my-project/dist/static"),
]
```

## Step 4: Run Django Server
You can see the Vue pages in http://127.0.0.1:8000/

# django-vuejs-hello

## Usage
```
cd frontend
npm install
npm run build
cd ..
./manage.py runserver
```

## Build from scratch
1. Initiate file hierarchy
```
django-admin startproject your_project
cd your_project
vue init webpack frontend
```

2. Configure django template directory and static files directory, modify `your_project/settings.py`
```
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['frontend/dist'], ##
        'APP_DIRS': True,
        ...
    },
]

...

STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "frontend/dist/static"),
]
```

3. Configure django url patterns, modify `your_project/urls.py`
```
urlpatterns = [
    path('admin/', admin.site.urls),
    re_path(r'^(?P<path>.*)$', TemplateView.as_view(template_name='index.html')) ##
]
```

django 1.0 use `url` function instead
```
    url(r'^$', TemplateView.as_view(template_name='index.html'))
```

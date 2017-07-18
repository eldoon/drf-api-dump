#drf-api-dump
This django app is intended for **dump data from apps or models via HTTP**.
Basically exposes dumdata command via http for custom needs. (just for superusers)

**Features**:
- Just accesible by superusers
- Ability to include or exclude any specific app or model

**Requirements**:
- Django (Developed under v1.11)
- Django Rest Framework (Developed under v3.4.3) 

##Installation
via pip from command line:
```shell
$ pip install -e git+[url_to_git_repo]
```
or include into requirements file as:
```
Django==1.11
...
-e git+[url_to_git_repo]
...
```

##Configuration
####urls.py:
Simply add a route like this in urlpatterns
```python
urlpatterns = [
    ...
    url(r'^your-route-to-drf-dump-api/', include('drf_api_dump.urls', namespace='drf-api-dump'))
]
```
####settings.py
Add this lines to your settings.py if you need some customizations
```python
# If you want to limit available apps and models to dump use DRF_API_DUMP_AVAILABLE
# Sets a list or tuple with app names or app.model.
# i.e.: Suppose you want to limit access to app auth (complete) and model token from
# authtoken app:
DRF_API_DUMP_AVAILABLES = ('auth', 'authtoken.token') 

# If you want to exclude any app or model use DRF_API_DUMP_EXCLUDE setting a list or tuple
# with app names or app.model names to exclude.
# i.e.: Suppose you want to exclude auth.permission model from dumps
DRF_API_DUMP_EXCLUDES = ('auth.permission')

# If you want to serve all apps and models, simply comment or delete those lines.

# If you want to change the view title
DRF_API_VIEW_TITLE = 'My customized view title'
```

This package has been written and released by David Vicente Ranz on July 2017

That's all folks!
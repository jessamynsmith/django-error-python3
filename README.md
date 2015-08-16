This is an example of the Django 1.8 / Python 3 issue when an app does not have an __init__.py file

I created this project by doing startproject and then startapp, then removing the __init__.py file
in the new app, adding the new app to INSTALLED_APPS.

When I try to run python manage.py, I get the following:

    $ python manage.py 
    Traceback (most recent call last):
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/apps/config.py", line 103, in create
        entry = module.default_app_config
    AttributeError: 'module' object has no attribute 'default_app_config'
  
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "manage.py", line 10, in <module>
        execute_from_command_line(sys.argv)
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/core/management/__init__.py", line 338, in execute_from_command_line
        utility.execute()
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/core/management/__init__.py", line 312, in execute
        django.setup()
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/__init__.py", line 18, in setup
        apps.populate(settings.INSTALLED_APPS)
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/apps/registry.py", line 85, in populate
        app_config = AppConfig.create(entry)
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/apps/config.py", line 106, in create
        return cls(entry, module)
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/apps/config.py", line 40, in __init__
        self.path = self._path_from_module(app_module)
      File "/Users/jessamyn/.virtualenvs/django_error_py3/lib/python3.4/site-packages/django/apps/config.py", line 69, in _path_from_module
        "with a 'path' class attribute." % (module, paths))
    django.core.exceptions.ImproperlyConfigured: The app module <module 'no_init' (namespace)> has multiple filesystem locations (['/Users/jessamyn/Development/django_error_py3/django_error_py3/no_init', '/Users/jessamyn/Development/django_error_py3/django_error_py3/no_init']); you must configure this app with an AppConfig subclass with a 'path' class attribute.

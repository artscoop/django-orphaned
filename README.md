# About django-orphaned
Django orphaned deletes every file in media subfolders not referenced anymore by a database entry.
To make things short, it clears orphaned files from the filesystem.

# Setup
install the package via easy_install or pip

    easy_install django-orphaned

with pip

    pip install django-orphaned
    
or

    pip install git+https://github.com/artscoop/django-orphaned --upgrade

then add it to installed apps in django settings.py

    INSTALLED_APPS = (
        ...
        'django_orphaned',
        ...
    )

now add this to your settings.py ('app' is your project name where models.py is located):

    ORPHANED_APPS_MEDIABASE_DIRS = {
        'app': {
            'root': [MEDIABASE_ROOT, MEDIABASE_ROOT2],  # MEDIABASE_ROOTn => default locations of your uploaded items e.g. /var/www/mediabase
            'skip': (               # optional iterable of subfolders to preserve, e.g. sorl.thumbnail cache
                path.join(MEDIABASE_ROOT, 'cache'),
                path.join(MEDIABASE_ROOT, 'foobar'),
            )
        }
    }

the least to do is to run this command to show all orphaned files

    python manage.py deleteorphaned --info

check the output satisfies your requirements then delete all orphaned files

    python manage.py deleteorphaned

# license
MIT-License, see [LICENSE](/ledil/django-orphaned/blob/master/LICENSE) file.

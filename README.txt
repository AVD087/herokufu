============
herokufu
============

by John Mark Schofield (jms@schof.org)

Provides common utility functions for Django projects on Heroku.

(It's heroku-fu as in Kung Fu, not as in F-U.)



IMPORTANT NOTE:
Please check the version number. This is pre-1.0 software. It's useful as examples of what I'm doing, but not yet ready for general-purpose production. (We're using it in production, but slight differences from our setup may break it.)


Requirements:
You must have vagrant and virtualbox and virtualenvwrapper installed.


Suggested installation workflow:

* Make project directory:
mkdir ~/versoncontrol/PROJECT
cd ~/versioncontrol/PROJECT
git init
django-admin.py createproject or mezzanine createproject
hfu init
edit files in settings directory




Offers the command hfu.

Examples:
Major (required) commands are:

  action to take
  -e / --environment -- environment to affect


up: Creates (if necessary), configures, and deploys a complete environment, including uploading static files. (local uploads to same static file server as staging)
hfu up -e local
hfu up -e staging
hfu up -e prod (For production, does test, then ups prod.)
hfu up -e test

manage: Allows you to run manage.py commands in a particular environment
hfu manage -e local -o [ createdb / syncdb / migrate / etc. ]
hfu manage -e staging -o [ createdb / syncdb / migrate / etc. ]
hfu manage -e prod -o [ createdb / syncdb / migrate / etc. ]
hfu manage -e test -o [ createdb / syncdb / migrate / etc. ]

destroy: Use with caution. Destorys an environment, good for keeping you from being charged for it.
hfu destroy -e local
hfu destroy -e staging
hfu destroy -e prod
hfu destroy -e test

test: Runs your test suite
hfu test (ups test, runs test)

reset: Destroys and then ups an environment.
hfu reset -e local
hfu reset -e staging
hfu reset -e prod
hfu reset -e test

revert: Revert to the state prior to the most recent "up." Does not apply to local.
hfu revert -e staging
hfu revert -e prod
hfu revert -e test

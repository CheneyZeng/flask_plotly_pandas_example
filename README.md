# flask_plotly_pandas_example

Instructions Deploying from the Classroom
Here is the code used in the screencast to get the web app running:

First, a new folder was created for the web app and all of the web app folders and files were moved into the folder:

```Python
mkdir web_app
mv -t web_app data worldbankapp wrangling_scripts worldbank.py
```

The next step was to create a virtual environment and then activate the environment:

```Python
conda update python
python3 -m venv worldbankvenv
source worldbankenv/bin/activate
```

Then, pip install the Python libraries needed for the web app

```Python
pip install flask pandas plotly gunicorn
```

The next step was to install the heroku command line tools:

```Python
curl https://cli-assets.heroku.com/install-ubuntu.sh | sh
https://devcenter.heroku.com/articles/heroku-cli#standalone-installation
heroku —-version
```

And then log into heroku with the following command

```Python
heroku login
```

Heroku asks for your account email address and password, which you type into the terminal and press enter.

The next steps involved some housekeeping:

```Python
remove app.run() from worldbank.py
```Python

type cd web_app into the Terminal so that you are inside the folder with your web app code.
Then create a proc file, which tells Heroku what to do when starting your web app:

```Python
touch Procfile
```

Then open the Procfile and type:

```Python
web gunicorn worldbank:app
```

Next, create a requirements file, which lists all of the Python library that your app depends on:

```Python
pip freeze > requirements.txt
```

And initialize a git repository and make a commit:

```Python
git init
git add .
git commit -m ‘first commit’
```

Now, create a heroku app:

```Python
heroku create my-app-name
```

where my-app-name is a unique name that nobody else on Heroku has already used.

The heroku create command should create a git repository on Heroku and a web address for accessing your web app. You can check that a remote repository was added to your git repository with the following terminal command:

```Python
git remote -v
```

Next, you need to push your git repository to the remote heroku repository with this command:

```Python
git push heroku master
```

Now, you can type your web app's address in the browser to see the results.

---
tags: py4web
published: true
comments: true
---

# How to easily install py4web on PythonAnywhere

---
>> "This article was originally published by Tom Campbell @tomcam [here](https://github.com/tomcam/py4webcasts/blob/master/docs/how-install-source-pythonanywhere.md). I've just added more stuff, updated it, and added other screenshots. Thanks Tom!"
---

One of the easiest ways to learn and play with [py4web](https://py4web.com) is to create a
free account on [PythonAnywhere](https://pythonanywhere.com). While
PythonAnywhere has ready-to-go  presets for other frameworks, such as 
webp2y or Django, you'll have to manually install py4web yourself.

This tutorial shows you step by step how to install and run the latest py4web framework from source.
It is meant for people with limited system administration knowledge, and it shouldn't leave anything out. 

### Important note: If this doesn't work, please leave a comment

## Create a PythonAnywhere account

If you still don't have one, you need to create a (free) PythonAnywhere account. They don't require a credit card, which 
means it's also practical for developers without good access to an American payment system. 

PythonAnywhere generously allows you to create a full working account for free, allowing you to create py4web apps.
You don't need a credit card to create the free account, and be sure that they will not ask you anything.

* Visit [PythonAnywhere](https://www.pythonanywhere.com/pricing/) and choose **Create a Beginner Account**

![Screenshot showing Creating a Beginner account](/img/py4web-on-pythonanywhere/Create_Account.png)

If you're using the free account, remember that your **username **will also be your subdomain (the first part of your public URL). So
choose it carefully: if your username is `your_username`, the base URL will be `your_username.pythonanywhere.com` and your web site
will be:

```
https://your_username.pythonanywhere.com
```

* Check the terms and conditions box and choose **Register**.

You're given brief online tour of PythonAnywhere.

* Choose **End Tour** when you're done.


## Go to the PythonAnywhere dashboard

Let's make sure we're on the same page, which should the the dashboard.

* Choose the [PythonAnywhere logo](https://www.pythonanywhere.com/) at the top of the page to navigate to the PythonAnywhere dashboard.

You'll see a navigation menu near the top of the page that says **Dashboard  Consoles  Files  Web  Tasks  Databases**. Choose the Dashboard navigation menu link.

![Screenshot showing Pythonanywhere web menu](/img/py4web-on-pythonanywhere/dashboard.png)

## Installing py4web from source on pythonanywhere

This section shows how to clone the py4web repo
from GitHub. It uses the Bash command line console supplied with PythonAnywhere.

### Start the bash console

PythonAnywhere lets you run a bash console directly in your browser.
That means you don't have to install and configure ssh to remote in: just run bash from 
their web page. You can perform many common tasks as if it were happening on your
own desktop without having to fiddle with ssh configuration.

From the navigation menu:

1. choose **Consoles**.

You'll see **Start a new Console**.

2. choose **Bash**.

![Screenshot showing Pythonanywhere web menu](/img/py4web-on-pythonanywhere/console.png)


After a few seconds, the Bash prompt appears in a new browser tab. It looks roughly like this: `~ $`.

![Screenshot showing Pythonanywhere web menu](/img/py4web-on-pythonanywhere/console_bash.png)

## Clone the GitHub repo

The next step is to obtain a copy of the py4web distribution. The following copies the latest
supported major release into its own directory.

* Enter `git clone https://github.com/web2py/py4web.git` at the prompt:

```bash
$ git clone https://github.com/web2py/py4web.git
```

A list of progress messages scrolls down. It looks something like this, but longer:

```
Cloning into 'py4web'...
remote: Enumerating objects: 167, done.
remote: Counting objects: 100% (167/167), done.
...
Checking out files: 100% (660/660), done.
04:21 ~ $ 
```
The result is a `py4web` subdirectory in your root directory containing the py4web source treee.

### Change to the py4web directory and install requirements using pip

Make py4web the current directory:

```bash
$ cd py4web
```

* Enter **python3 -m pip install -U --user -r requirements.txt** to install py4web using pip:

```bash
# --U updates old modules.
# --user means install in your local directory 
#   Required on PythonAnywhere because you don't have 
#   permission to install globally.
$ python3 -m pip install -U --user -r requirements.txt
```

### Setup py4web itself

Now configure py4web:

```bash
$ ./py4web.py setup apps
$ ./py4web.py set_password
```

The `./py4web.py set_password` step asks you twice for a password. That will be used when you log into the py4web dashboard.

## Open a second tab for PythonAnywhere

You currently have a web page open running a simulated bash console for py4web. Open a second PythonAnywhere tab.

* There's a PythonAnywhere logo at the top of the page. Right-click (or Command-Click on MacOS) that logo to 
open another PythonAnywhere page.

## Go to the WebApps page and create a new web app


* On the navigation bar near the top of the page choose **Web** and then **Add a new web app**:

![Screenshot showing Pythonanywhere web menu](/img/py4web-on-pythonanywhere/web_menu.png)

* A dialog appears called  **Create a new web app**

You're informed that PythonAnywhere is creating a URL for your site and displays that URL. The main part of the URL is your username followed by `pythonanywhere.com`.

![Screenshot showing Pythonanywhere new web app](/img/py4web-on-pythonanywhere/new_webapp.png)

* Choose **Next**.

### Choose the Bottle framework

The **Select a Python Web framework**  dialog appears, showing a list of frameworks like web2py, Django, Bottle, and so on.

Py4web uses [Bottle](http://bottlepy.org). So:

* Choose **Bottle** from the list.

![Screenshot showing Pythonanywhere bottle](/img/py4web-on-pythonanywhere/bottle.png)

You're asked to select a Python version.

* Choose **Python 3.10** (or later versions if available):

![Screenshot showing Python 3.x and Bottle being selected](/img/py4web-on-pythonanywhere/python.png)

The **Quickstart new Bottle Project** dialog appears. You're asked to give the location where a `bottle_app.py` file will be generated. 
It looks something like this, where `your_username` stands in for the PythonAnywhere username you created on signup.

```bash
Path:
/home/your_username/mysite/bottle_app.py
```

* Replace the `mysite` portion with `py4web`. 

* Replace `your_username` with your PythonAnywhere username. 

For example:

```bash
/home/your_username/py4web/bottle_app.py
```

* Choose **Next**.

You're shown a message saying `All done! Your web app is now set up. Details below.`



## Change your site's working directory

* Scroll down to the section headed **Code**, which shows **Source Code**, **Working Directory**, and other information.

### Make your py4web folder both the source code and working directory by replacing mysite

* Click the URL next to **Source Code**. It is made editable. Make sure the end contains your URL followed by `/py4web` intead of `/mysite`. 
Replace `your_username` in the following example with your PythonAnywhere username, and after typing in the correct values
**be sure to click the checkmark button** to confirm your changes:

```
# 1. Replace your_username with your own PythonAnywhere username
# 2. Replace mysite with py4web
# 3. BE SURE to click the checkmark to confirm your change!
/home/your_username/py4web
```

* Do the same for **Working directory**.

### Update your WSGI configuration file 

The WSGI configuration needs your project's home directory updated from its default value. Just under **Source code** and **Working directory** you'll see **WSGI configuration file**. 
You can open up a built-in editor for it simply by clicking.

* Click the link for **WSGI configuration file** and your WSGI configuration file appears in an editor.

You'll see something like this, with your PythonAnywhere username in place of `your_username`:

```
project_home = '/home/your_username/mysite'
```

* Change it to your py4web apps folder name like this, replacing `your_username` with your PythonAnywhere username, and replacing `mysite` with `py4web/apps` Make sure it all
stays within the quote marks:

```
project_home = '/home/your_username/py4web/apps'
```

* At the top of the page choose **Save** to preserve your changes.

### Update bottle_app.py

* Return to the PythonAnywhere bash shell.

Run your favorite editor on the file `~/py4web/bottle_app.py`:

```bash
# Replace vim with whatever editor you prefer
vim ~/py4web/bottle_app.py
```

* Replace the contents of `bottle_app.py` as follows

```
import os
from py4web.core import wsgi

# BEGIN CONFIGURATION
PASSWORD_FILENAME = 'password.txt'
DASHBOARD_MODE = 'full' or 'demo' or 'none'
APPS_FOLDER = 'apps'
# END CONFIGURATION

password_file = os.path.abspath(os.path.join(os.path.dirname(__file__), PASSWORD_FILENAME))
application = wsgi(password_file=password_file, 
                   dashboard_mode=DASHBOARD_MODE,
                   apps_folder=APPS_FOLDER)
```


### Reload your web app

* Return to the PythonAnywhere **Web** page

There is now a **Configuration** section with the name of your URL, and a big green **Reload** button with your URL on it.

* Choose the **Reload your_username.pythonanywhere.com** button, where your_username is used in place of your PythonAnywhere account name.

A progress icon appears for a few seconds, then the page returns to its previous state. You're finally ready to run py4web.

## Start py4web

* Return to the PythonAnywhere bash shell.

* Start py4web like so:

```bash
$ ./py4web.py run apps
```

This starts the built-in py4web web server and runs its own copy of the py4web site. It is now available
online at your PythonAnywhere URL.

## Visit your website

* Return to the PythonAnywhere **Web** page: on the navigation bar near the top of the page that says **Dashboard  Consoles  Files  Web  Tasks  Databases** choose **Web**.

Near the top you'll see **Configuration for** and the URL of your website in link form.

* Click your website's URL under  **Configuration for**.

It should look like this:

![Screen shot of the py4web home page](/img/py4web-on-pythonanywhere/py4web-home.png)

To begin writing py4web apps choose **Dashboard**.

* You'll be asked for the password you created earlier. When you enter it you'll see the py4web dashboard:

![Screen shot of the py4web home page](/img/py4web-on-pythonanywhere/py4web-dash.png)


Notice: if you should notice some tickets inside the py4web dashboard with errors like " "module 'lib' has no attribute 'X509_V_FLAG_NOTIFY_POLICY'",
you can easily resolve by upgrading the OpenSSL python libraries provided by PythonAnywhere with the bash command:

```bash
$ pip3 install pyOpenSSL --upgrade
```

Don't forget to reload the py4web application using the Web main menu on PythonAnywhere, as shown before.



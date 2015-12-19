# Part B - Baby Steps

#### tl;dr

[insert picture of hello world webpage]

Create a server that displays hello world

## Hello World

#### tl;dr

`source venv/bin/activate`

`touch views.py`

*Edit views.py*

`python views.py`

#### Hello world server

First things first, we are going to need to get a server up and
running. Hopefully everything from the last part works already.

Start up your favourite editor (personally I use emacs, but I don't
judge. Just don't use windows notepad). We create the file `views.py`
to store what we will call our **views**.

The contents of the file should look like this:

```python
from flask import Flask

app = Flask(__name__)
app.debug = True

@app.route('/hello')
def hello():
    return 'Hello World!'

if __name__ == '__main__':
   app.run()
```

Lets go through all of the bits of this example before moving on

```python
from flask import Flask
```

This imports something from flask. If you are familiar with import
statements you know that in the file `flask.py` there is something
with the name `Flask` that we now can use in our file. The `flask.py`
code is of course located inside our virtualenv which you really
should activate if you have not done so yet

```python
app = Flask(__name__)
app.debug = True
```

This creates our app (basically a server). The second line is there
for debugging purposes. `__name__` is a special thing in python. When
your run a program python will set this to what it thinks is
appropriate. Generally it is used to check if the current module is
being imported or run directly.

```python
@app.route('/hello')
def hello():
    return 'Hello World!'
```

The first line registers a view in the server. By doing this we
essentially tell flask that when someone accesses
www.my_cool_but_fake_website.com/hello from a browser we want the
function `hello` to handle that access. `hello` itself is a simple
function that returns the string `"Hello World!"`


```python
if __name__ == '__main__':
   app.run()
```

The first is a standard line of code in python. It translated to "If
someone ran this from the command line". It is used to see the
difference between an import of a python file and running the file
from the command line.

#### What is this view thing that he keeps talking about?

In flask (and a lot of other web development) you often talk about
views. A view is a page that you can access with the browser. For
normal™ people it doesn't make sense to talk about views, just
webpages. But for programmers a webpage is not necessarily served,
just any `.html` file is a webpage. A view on the other hand is
something that **is** displayed to the user. 

In this tutorial I will sometimes talk about "the views" and then I
will generally mean the functions defined in `views.py` with an
`@app.route('/somestring')` in front of them.

#### Running the server

In order to run the server you should run `python views.py` on the
commandline. Fire up your favourite browser (I use Firefox, but I
don't judge. Just don't use Internet Explorer) and type
`localhost:5000/hello` into the webpage bar (not the small search bar, the
big one). `localhost` means "this machine" and 5000 is the port you use
to connect to the server. Flask defaults to using port 5000.

You should now see the incredibly dull but extremely rewarding phrase
"Hello World!" on your screen. 

## Directory Structure.

After doing all this your directory should look something like this:

```
├── venv
└── views.py
```
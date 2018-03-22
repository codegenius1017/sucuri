# Sucuri
Simple and efficient Template Engine for Python projects

## Instaling
Install and update using [pip](https://pip.pypa.io/en/stable/quickstart/):
> pip install sucuri

## Creating a Sucuri Template
Example of code:
```
html
    body
        h1 Title
        a(href='#') This is my link
```
As can be seen in the code example above, the sucuri development requires tabulation standardization. We do not determine the number of spaces, but it is necessary to keep the same number of spaces on the left in the whole code, because this quantity will inform if a certain TAG of the HTML will be contained within another one or not. With this, in the example above we will have the following HTML code:
```
<html>
    <body>
        <h1>Title</h1>
        <a href="#">This is my link</a>
    </body>
</html>
```

## Using
To use sucuri, you need to import the sucuri package into your Python file, the example below is an application that uses the sucuri to render in the [Flask](http://flask.pocoo.org/):
```
from sucuri import rendering
from flask import Flask, render_template_string

app = Flask(__name__)

@app.route("/")
def index():
    template = rendering.template('template.suc')
    return render_template_string(template)
```

As can be seen in the example above, the template in the example is loaded from a file named `template.suc` which is in the project's root directory, however it could be in any project directory, such as `templates/template.suc` if you include a folder to group the templates.

### Text
In sucuri, texts are described in two ways. It can be written after the declaration of the tag such as:
```
h1 Title
```
Result:
```
<h1>Title</h1>
```
Or you can type in more than one line using the | on the lines that are not the same as the tag, see example:
```
h3 Hello!
    | Text
    | with
    | more than
    | one line
```
Result:
```
<h3>Hello!
    Text
    with
    more than
    one line
</h3>
```
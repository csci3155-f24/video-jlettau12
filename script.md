Using Flask to Learn Functional Programming Principles in Python

Hello and welcome to this tutorial. Today, we’ll explore functional programming principles, specifically using functions as values, while building a To Do List app using the software framework Flask in Python. 
Assuming you already have python and pip installed, flask is not difficult to get. On Windows, just open your terminal and run “python -m pip install flask”. This is all you need to run the dedicated web pages I will be building in this tutorial.

While I type up a quick flask Hello World test, let’s go over the basic class concept of today's tutorial, which is using
Functions as Values: Functions can be treated as variables, allowing us to pass them around. Flask is a framework that makes use of this concept very often, as you will see in the following video.

When we run the test program, it will give us a link to a web server that will be running our code, as you can see, the hello world test works just fine.



Step Two: Initialize files
Let’s start the project. First, we want to make a folder for the project, lets call it toDoApp, and add a main python file to it. Let’s call it app.py. We will start with a basic flask framework you can find in any python file using flask. 
Then, since we are using Flask on a folder called templates, we have to make this folder in the toDoApp directory.
As you can see, we are going to be working with a file called index.html. In the newly created templates folder, we can add this file. We then need to add the basic html framework, simply consisting of the heading, title, and body.
<!DOCTYPE html>
<html lang = "en">
<head>
    <meta charset="UTF-8">
    <title>
       To Do Project
    </title>
</head>
<body>
    <h1>To Do List</h1>
</body>
</html>


Step Three: Initialize a spot for the todos to go
Now, in our app.py file, we want to add a sample todo below the heading, just to test some things out and get a list object going for our todos. We will just call it sample todo and of course done will always be false when a list element is initialized

from flask import Flask, render_template, request, redirect, url_for


app = Flask(__name__, template_folder='templates')


todos = [{"task": "Sample ToDo", "done": False}]


@app.route('/')
def index():
    return render_template('index.html', todos = todos)


if __name__ == '__main__':
    app.run(debug=True)





Back in the index file, we want to set up a section to list the todos with a for function. Let’s test what we have so far. As you can see, the site successfully lists our 1 todo list sample element.
<!DOCTYPE html>
<html lang = "en">
<head>
    <meta charset="UTF-8">
    <title>
       To Do Project
    </title>
</head>
<body>
    <h1>To Do List</h1>
    <ul>
        {%for todo in todos%}
            <li>{{todo[‘task’]}}</li>
        {%endfor%}
    </ul>
</body>
</html>

Step Four: Code the framework in python for adding, editing, and deleting list elements

from flask import Flask, render_template, request, redirect, url_for


app = Flask(__name__, template_folder='templates')


todos = [{"task": "Sample ToDo", "done": False}]


@app.route('/')
def index():
    return render_template('index.html', todos = todos)


@app.route('/add', methods=['POST'])
def add():
    todo = request.form['todo']
    todos.append({"task": todo, "done": False})
    return redirect(url_for('index'))


@app.route('/edit/<int:index>', methods=['GET', 'POST'])
def edit(index):
    todo = todos[index]
    if request.method == 'POST':
        todo['task'] = request.form['todo']
        return redirect(url_for('index'))
    else:
        return render_template('edit.html', todo=todo, index=index)
   
def toggle_task(task):
    task['done'] = not task['done']


@app.route('/check/<int:index>')
def check(index):
    toggle_task(todos[index])
    return redirect(url_for('index'))


@app.route('/delete/<int:index>')
def delete(index):
    del todos[index]
    return redirect(url_for('index'))


if __name__ == '__main__':
    app.run(debug=True)

HIGHLIGHTED IN PINK: Alright, Here is an example we can connect to our course content in principles of programming languages. It is an implementation of using functions as values:  In Python, we can treat functions like any other value. For example, we can pass a function to another function to encapsulate logic and make our code reusable. By defining toggle_task as its own function, we can reuse it in other parts of the app if needed, such as a toggle everything feature. Here, we use it in the check function to see if a task is checked or not. This demonstrates how functions can be passed and used just like variables.

Now, we want to head back to our html file to add the functionality to add a todo to the list.
<!DOCTYPE html>
<html lang = "en">
<head>
    <meta charset="UTF-8">
    <title>
       To Do Project
    </title>
</head>
<body>
    <h1>To Do List</h1>
    <ul>
        {%for todo in todos%}
            <li>{{todo['task']}}</li>
        {%endfor%}
    </ul>
    <form action="{{url_for('add')}}" method="post">
        <input type="text" name="todo">
        <button type="submit">Add Todo</button>
    </form>
</body>
</html>

When we run and test this, we can see it successfully adds tasks to the list. However, we don’t want it to just display the name of what we enter - we obviously want the capabilities that a to do list should have. So, let’s head to our index file and add checkboxes, as well as buttons to edit and delete list elements.
<!DOCTYPE html>
<html lang = "en">
<head>
    <meta charset="UTF-8">
    <title>
       To Do Project
    </title>
</head>
<body>
    <h1>To Do List</h1>
    <ul>
        {%for todo in todos%}
                    {%endfor%}
    </ul>
    <form action="{{url_for('add')}}" method="post">
        <input type="text" name="todo">
        <button type="submit">Add Todo</button>
    </form>
</body>
</html>

This does successfully add the buttons, and delete even works already. However, edit does not function correctly, and we do not have a check button. This is a bug that will be fixed later. For now, let’s implement edit’s functionality.

So, we need to make a template file called edit.html. It’s a very simple one, here’s how its implemented.
<!DOCTYPE html>
<html lang = "en">
    <head>
        <meta charset="UTF-8">
        <title>
           
        </title>
    </head>
    <body>
        <form action="{{url_for('edit', index=index)}}" method="post">
            <input type="text" name="todo" value = "{{todo['task']}}">
            <button type="submit">Save</button>
    </body>
</html>

At this point you can see we have a mostly functional to do list. However, as mentioned earlier, there is a bug with the check function. I simply forgot to add the line to add the button to each list element. After that is fixed, everything should work!

